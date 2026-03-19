# Validación de usuario con XML, XSD y expresiones regulares

## Expresiones Regulares y Restricciones
Se han diseñado las siguientes expresiones regulares para cumplir con los requisitos establecidos, utilizando Regex101 para su validación:

1. **Email:** `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$`
   * Permite caracteres alfanuméricos y símbolos seguros antes de la arroba, seguidos de un dominio válido y un TLD de al menos dos letras.
2. **Teléfono (España):** `^(\+34|0034)?[6789]\d{8}$`
   * El prefijo internacional es opcional. Obliga a que el número nacional comience por 6, 7, 8 o 9, seguido de 8 dígitos adicionales.
3. **Código Postal (España):** `^(0[1-9]|[1-4][0-9]|5[0-2])\d{3}$`
   * Valida los códigos que van desde el 01 al 52, exactamente con tres dígitos después.
4. **Nombre de Usuario:** `^[a-z][a-zA-Z0-9]+$`
   * Obliga a iniciar con una letra minúscula, seguida de uno o más caracteres alfanuméricos.
5. Contraseña:** * La contraseña debe tener al menos 8 caracteres y contener mayúsculas, minúsculas, dígitos y símbolos.
   * **Patrón estricto (Regex101):** `^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&_])[A-Za-z\d@$!%*?&_]{8,}$` (Utiliza *lookaheads* para obligar la presencia simultánea de todos los grupos).
   * **Patrón en el XSD:** Dado que el estándar XSD 1.0 no soporta aserciones complejas (*lookaheads*), el esquema aplica la restricción básica de caracteres permitidos y longitud mínima: `[a-zA-Z0-9@$!%*?&_]{8,}` aplicándolo directamente a un tipo simple basado en `xs:string`.
