using System;
					
public class Program
{
	public static void Main()
	{
		Console.WriteLine("Nombre de la tienda");
		Console.WriteLine();
		Console.WriteLine("opciones");
		Console.WriteLine();
		Console.WriteLine("1. Buscar Producto");
		Console.WriteLine();
		Console.WriteLine("2. Suma Rapida de Productos");
		Console.WriteLine();
		Console.WriteLine("3. Pagar Cuenta");
		Console.WriteLine();
		Console.WriteLine("4. Consultar Cuenta del CLiente");
		Console.WriteLine();
		Console.WriteLine("5. Actualizar Cuenta de Cliente");
		Console.WriteLine();
		Console.WriteLine("6. Calcular Informe de Ventas");
		Console.WriteLine();
		Console.WriteLine("7. Calcular Cartera del Cliente");
		Console.WriteLine();
		Console.WriteLine("8. Cuentas por Pagar");
		Console.WriteLine();
		Console.WriteLine("9. Salir");
		while(Ejecucion)
		{
			Console.WriteLine();
			Console.WriteLine("Ingrese un Numero");
			string Selecion = Console.ReadLine();
		
			switch (int.Parse(Selecion))
			{
				case 1://Buscar Producto
					
				break;

				case 2://Suma Rapida de Productos
					
				break;
						
				case 3: // Pagar cuenta
						
				break;

				case 4: // consultar cuenta client
					
				break;

				case 5: // Actualizar cuenta cliente
				
				break;
				case 6:// Informe de ventas
					
				break;
				
				case 7:
				
				break;

				case 8:

				break;

				case 9://Salir
					
				break;

				default: 
					Console.WriteLine("Se ingreso un valor por fuera del rango");
				break;
			}
		}
	}
}
	}
  
  }
