# OOP-Ejercicio2
Desarrollar un programa en Java que gestiona la información de una entidad bancaria:
  1. El objeto PersonaFisica consiste en:
    a) Propiedades: nif, nombre, apellidos, nóminaDomiciliada, dirección, IBAN, importeNómina, valoraciónCliente, solicitudCredito.
    b) Métodos:
      • Constructor: Parámetros para inicializar sus propiedades excepto el iban, la valoración de cliente y la solicitud de crédito
      • Constructor: Parámetros para inicializar todas sus propiedades, excepto la valoración de cliente y la solicitud de crédito.
      • Representación en cadena del objeto.
      • Establecer el valor de sus propiedades.
      • Obtener el valor de sus propiedades.
      • Obtener una copia del objeto.
  2. El objeto Empresa consiste en:
    a) Propiedades: nif, razón social, tipo (SA, SL, Autónomo), actividad, IBAN, valoraciónCliente, solicitudCredito.
    b) Métodos:
      • Constructor: Parámetros para inicializar sus propiedades excepto el iban, la valoración del cliente y la solicitud de crédito.
      • Constructor: Parámetros para inicializar todas sus propiedades excepto la valoración del cliente y la solicitud de crédito.
      • Establecer el valor de sus propiedades.
      • Obtener el valor de sus propiedades. 
  3. El objeto IBAN consiste en:
    a) Propiedades: país (2 caracteres en mayúscula), código de control (2 dígitos), entidad (4 dígitos), oficina (4 dígitos), dígito de control (2 dígitos), numeroCuenta (10 dígitos), saldo, %saldoNegativo, fechaApertura. 
    b) Métodos:
      • Constructor: Parámetros para inicializar todas sus propiedades.
      • Establecer el valor de sus propiedades.
      • Obtener el valor de sus propiedades. 
      • Calcular y obtener el tiempo de la cuenta en años, meses y días.
      • Representación en cadena del objeto.
      • Copia de objeto.
  4. El objeto SolicitudCrédito consiste en:
    a) Propiedades: 
      • id, capital (máximo 50000 € para prestamo personal, 250000 € parapréstamo hipotecario y 1000000 € para préstamo de empresa), tipo (personal, hipotecario, empresa), fechaSolicitud, moneda (€ o $) y plazo (meses). 
      • tipo de interés (fijo, variable), %interés fijo, índice de referencia (Euribor, IRS, IRPH Bancos, IRPH Cajas, Mibor), %diferencial, periodoRevisión (número de meses), plazo (meses) y fechaEstablecimiento.
    b) Métodos:
      • Constructor: Parámetros para inicializar el id, capital, tipo, fechaSolicitud, moneda y plazo.
      • Establecer el valor de sus propiedades (excluyendo las propiedades relativas al pago del préstamo, que son calculadas mediante método de la interfaz).
      • Obtener el valor de sus propiedades. 
      • Calcular y obtener la fecha de vencimiento.
      • Representación del objeto en cadena de caracteres que distinga entre un préstamo a interés fijo o variable.
      • Copia de objetos.
  5. La Interfaz EstimacionVariablesCredito se implementa en PersonaFisica y Empresa.
    Consiste en los siguientes métodos:
    a) asignarValoracion(). Se estima y asigna una valoración de cliente a un cliente (persona física o empresa) mediante una categoría que puede ser A (menor riesgo), B o C (mayor riesgo). Si es Persona física:
      • Si es un préstamo personal y su nómina es menor de 1300 € es C.
      • Si es un préstamo personal y su nómina está entre 1300 € y 2500 € y el capital es mayor de 20000 € es B.
      • Si es un préstamo personal y su nómina está entre 1300 € y 2500 € y el capital es menor de 20000 € es A.
      • Si es un préstamo personal y su nómina es superior a 2500 € es A.
      • Si es un préstamo hipotecario y su nómina es menor de 1300 € es C.
      • Si es un préstamo hipotecario, su nómina es mayor de 1300 € y el capital es superior a 100000 € es B. 
      • Si es un préstamo hipotecario, su nómina es mayor de 1300 € y el capital es inferior a 100000 € es A. 
      Si es una Empresa:
      • Si el saldo de su cuenta es mayor de 50000 € y el tipo es SA es A.
      • Si el saldo de su cuenta es mayor de 50000 € y el tipo no es SA es B.
      • Si el saldo de su cuenta es menor de 50000 € y el tipo es SA es B.
      • Si es autónomo o no cumple los anteriores, el tipo es C.
    b) calcularInteres(). Se calcula y asigna un % para una solicitud de préstamo. Para una persona física es:
      • Para un préstamo personal: tipo de interés (fijo, variable), %interés fijo, índice de referencia (Euribor, IRS, IRPH Bancos, IRPH Cajas, Mibor), %diferencial, periodoRevisión (número de meses).
      • Si la valoración es A y el plazo superior a 5 años → Fijo 3%. 
      • Si la valoración es A y el plazo inferior a 5 años → Fijo 3,5%.
      • Si la valoración es B → Fijo 4%.
      • Si la valoración es C → Fijo 5%.
      • Para un préstamo hipotecario:
      • Si la valoración es A y el plazo inferior a 20 años → Variable Euribor + 1% con revisión cada 6 meses.
      • Si la valoración es A y el plazo mayor a 20 años → Variable Euribor + 2% con revisión anual.
      • Si la valoración es B y el plazo inferior a 20 años → Variable IRS + 1,5% con revisión anual.
      • Si la valoración es B y el plazo mayor a 20 años → Variable IRS + 2,5% con revisión cada 6 meses.
      • Si la valoración es C → Variable Mibor + 3% con revisión cada 6 meses. 
      Para una empresa:
      • Si la valoración es A y la cuenta tiene 10 años o más de antigüedad: 1,5 %
      • Si la valoración es A y la cuenta tiene menos de 10 años de antigüedad: 2,5%
      • Si la valoración es B y el plazo es 5 años o superior → 3%
      • Si la valoración es B y el plazo es inferior a 5 años → 3,5 %
      • Si la valoración es C → No hay interés, se deniega por alto riesgo.
