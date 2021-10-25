using System;
					
public class Program
{
	public static void Main()
	{
		bool Ejecucion = true;
		string [] Productos = {"Arepas", "Azucar", "Pan", "Jamon", "Leche", "Tortillas", "Queso", "Panela", "Chocolate", "Jabon"};
		int [] Precios = {2000,3000,2500,4500,3000,3500,1500,500,5000,6000};;
		int Total = 0;
		int [] CarritoPrecios = new int [0];
		string [] CarritoProductos = new string [0];
		int NProductos = 0;
		uint [] CuentasClientes = {1523648972,1423657890,1243598762,1253686547};
		int [] EstadoDeCuenta = {0,0,0,0};
		int Deuda = 0;
		
		Console.WriteLine("La Tienda del Barrio de don Lucho");
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
		Console.WriteLine("8. Salir");
		Console.WriteLine();
		Console.WriteLine("9. Creditos");
		Console.WriteLine();

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
					
					Console.WriteLine("La Cuenta tiene un valor de: " + Total);
					Console.WriteLine("Porfavor eleja un metodo de pago");
					Console.WriteLine("1. Pago en efectivo");
					Console.WriteLine("2. Fiar");
					string R = Console.ReadLine();
					
					if(int.Parse(R) == 1)
					{
						Console.WriteLine("¿Con cuanto va a pagar?");
						string Plata = Console.ReadLine();
						
						int Devuelta = int.Parse(Plata) - Total;
						Console.WriteLine("Su devuelta es de: " + Devuelta);
					}
					
					if(int.Parse(R) == 2)
					{
						Deuda = Total;
					}
					
						
				break;

				case 4: // consultar cuenta client
				
					Console.WriteLine("¿Usted ya tiene cuenta?");
					Console.WriteLine("1. Si");
					Console.WriteLine("2. No");
					string Cuenta = Console.ReadLine();
					
					if(int.Parse(Cuenta) == 1)
					{
						Console.WriteLine("Ingrese su ID");
						string ID = Console.ReadLine();
						for (int i = 0; i<CuentasClientes.Length; i++)
						{
							if(CuentasClientes[i] == uint.Parse(ID))
							{
								Console.WriteLine("La Cuenta: " + CuentasClientes[i] + " tiene un saldo de " + EstadoDeCuenta[i]);
							
								if(EstadoDeCuenta[i] < 0)
								{
									Console.WriteLine("Usted esta en deuda");
								}
							
								if(EstadoDeCuenta[i] == 0)
								{
									Console.WriteLine("Usted esta en paz y salvo");
								}
							
								if(EstadoDeCuenta[i] > 0)
								{
									Console.WriteLine("Usted ested tiene plata");
								}
							}
						}
					}
					
					if(int.Parse(Cuenta) == 2)
					{
						
						Console.WriteLine("Ingrese su ID");
						string IDNuevo = Console.ReadLine();
						
						Array.Resize<uint>(ref CuentasClientes, CuentasClientes.Length + 1  );
						Array.Resize<int>(ref EstadoDeCuenta, EstadoDeCuenta.Length + 1 );
						CuentasClientes[CuentasClientes.Length -1] = uint.Parse(IDNuevo);
						EstadoDeCuenta[ EstadoDeCuenta.Length -1] = 0;
						Console.WriteLine("Se Creo una nueva cuenta :D");
					}
					
				break;

				case 5: // Actualizar cuenta cliente
				
					Console.WriteLine("Ingrese su ID");
					string ID2 = Console.ReadLine();
					for (int i = 0; i<CuentasClientes.Length; i++)
					{
						if(CuentasClientes[i] == uint.Parse(ID2))
						{	
							EstadoDeCuenta[i] = -Deuda; 
							Console.WriteLine("La Cuenta: " + CuentasClientes[i] + " tiene un saldo de " + EstadoDeCuenta[i]);
						}
					}
					
				
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
					Console.WriteLine("Ingrese su ID");
					string ID3 = Console.ReadLine();
					for (int i = 0; i<CuentasClientes.Length; i++)
					{
						if(CuentasClientes[i] == uint.Parse(ID3))
						{
							
							if(EstadoDeCuenta[i] < 0)
							{
								Console.WriteLine("Usted esta en deuda por la cantidad de: " + EstadoDeCuenta[i]);
							}
							
							if(EstadoDeCuenta[i] == 0)
							{
								Console.WriteLine("Usted esta en paz y salvo");
							}
							
						}
					}
				
				break;

				case 8:
					Console.WriteLine("Vuelva Proto :D");
					Ejecucion = false;

				break;

				case 9://Creditos
					
					Console.WriteLine("Estudiantes de Ingenieria en Diseno de Entretenimiento Digital");
					Console.WriteLine("");
					Console.WriteLine("Fundamentos de Programacion");
					Console.WriteLine("");
					Console.WriteLine("Pablo Velez Mesa");
					Console.WriteLine("Juan Sebastian Giraldo Mosquera");
					Console.WriteLine("Yeison Andres Munoz Ceron");
				break;

				default: 
					Console.WriteLine("Se ingreso un valor por fuera del rango");
				break;
			}
		}
	

	}
  
  }
