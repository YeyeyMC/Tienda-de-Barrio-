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
					
					Console.WriteLine("Ingrese el nombre del producto");
					string Item = Console.ReadLine();
					bool ProductoEncontrado = false;
					for (int i = 0; i <Productos.Length; i++)
					{
						if(Productos[i].Equals(Item))
						{
							ProductoEncontrado = true;
							Console.WriteLine("El producto " + Productos[i] + " Tiene un valor de: " + Precios[i]);
							
						}
						else if (!ProductoEncontrado)
						{
							ProductoEncontrado = false;
						} 
						
					}
					
					if(!ProductoEncontrado)
					{
						Console.WriteLine("El producto que ingreso no existe");
					}
					
				break;

				case 2://Suma Rapida de Productos
				Console.WriteLine("Cuantos Productos desea Levar?");
					string R1 = Console.ReadLine();
					Array.Resize<int>(ref CarritoPrecios, CarritoPrecios.Length + int.Parse(R1));
					Array.Resize<string>(ref CarritoProductos, CarritoProductos.Length + int.Parse(R1));
					int TTotal = 0;
					for (int i = 0; i < int.Parse(R1); i++)
					{
						Console.WriteLine("Ingrese el nombre del producto");
						string Item2 = Console.ReadLine();
						bool ProductoEncontrado2 = false;
							for (int j = 0; j <Productos.Length; j++)
							{
								if(Productos[j].Equals(Item2))
								{
									ProductoEncontrado2 = true;
										Console.WriteLine("El producto " + Productos[j] + " Tiene un valor de: " + Precios[j]);
										TTotal += Precios[j];
										CarritoPrecios[NProductos] = Precios[j];
										CarritoProductos[NProductos] = Productos[j];
									NProductos ++;
								}
								else if (!ProductoEncontrado2)
								{
									ProductoEncontrado = false;
								} 
							}
					
							if(!ProductoEncontrado2)
							{
								Console.WriteLine("El producto que ingreso no existe");
							}
					}
					
					Console.WriteLine("La suma es de: " + TTotal);
					Total += TTotal;
				break;
						
				case 3: // Pagar cuenta
						
				break;

				case 4: // consultar cuenta client
					
				break;

				case 5: // Actualizar cuenta cliente
				
				break;
				case 6:// Informe de ventas
				
					Console.WriteLine("Usted a Comprado: ");
						for (int l = 0; l < CarritoPrecios.Length;l++)
					{
						Console.WriteLine(CarritoProductos[l] + " Tiene un precio de: " + CarritoPrecios[l]);
					}
						Console.WriteLine("La suma es de: " +Total);

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
