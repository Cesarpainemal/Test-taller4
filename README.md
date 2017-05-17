Scanner entrada = new Scanner (System.in);
        
        int numAlum = 0, cantNotas = 0;
        double suma = 0, promedio = 0, sumatotal = 0, promediototal = 0;
        double mayor, menor;
        
        System.out.print("Ingrese cantidad de alumnos");
        numAlum = entrada.nextInt();
        
        System.out.print("Ingrese cantidad de notas");
        cantNotas=entrada.nextInt();
        
        
            double [][] datos = new double [numAlum+3][cantNotas+3];
        
        
            double [] promedios = new double [numAlum];
        
        System.out.println("\n\n");
        for (int i =0;i<numAlum;i++){
            for (int j =0;j<cantNotas;j++){
                System.out.print("Ingrese la nota "+(j+1)+" del alumno "+ (i+1)+": ");
                datos[i][j]= entrada.nextInt();
            }
            System.out.print("\n");
        }
        
        System.out.println("\n\n\nCONCENTRACION DE NOTAS");
        System.out.println("---------------------------------");


        for (int i = 0; i < numAlum; i++){
            System.out.print("Alumno "+(i+1));
            for(int j =0;j<cantNotas;j++){
                System.out.print("   "+datos[i][j]);
           }
            System.out.print("\n");
        }

        System.out.println("\n\n\nDATOS POR ALUMNO");
        System.out.println("-----------------");
        
        for (int i = 0; i < numAlum; i++){
            
            suma = 0;
            mayor = datos [i][0];
            menor = datos [i][0];
            
            for(int j = 0; j < cantNotas; j++){
                
                suma += datos[i][j];
                
                if (datos[i][j] > mayor){
                    mayor = datos[i][j];
                }   
                
                if (datos[i][j] < menor){
                    menor = datos[i][j];
                }
            }
            promedio = suma/cantNotas;
            datos[i][cantNotas]=promedio;
            datos[i][cantNotas+1]=mayor;
            datos[i][cantNotas+2]=menor;

            System.out.println("\nEl promedio del alumno "+(i+1)+" es: "+promedio);
            System.out.println(" Su nota mayor es: "+mayor );
            System.out.println(" Su nota menor es "+menor );

            
            promedios[i] = promedio;
        }
        for (int i = 0; i < cantNotas; i++){
            
            suma = 0;
            mayor = datos [0][i];
            menor = datos [0][i];
            
            for(int j = 0; j < numAlum; j++){
                
                suma += datos[j][i];
                
                if (datos[j][i] > mayor){
                    mayor = datos[j][i];
                }   
                
                if (datos[j][i] < menor){
                    menor = datos[j][i];
                }
            }
            promedio = suma/numAlum;
            datos[numAlum][i]=promedio;
            datos[numAlum+1][i]=mayor;
            datos[numAlum+2][i]=menor;

            System.out.println("\nEl promedio de las notas "+(i+1)+" es: "+promedio);
            System.out.println(" Su nota mayor es: "+mayor );
            System.out.println(" Su nota menor es "+menor );

            
        }


        
        System.out.println("\n\n\nLISTADO DE NOTAS AZULES: ");
        System.out.println("-------------------------");

        for (int i = 0; i < numAlum; i++) {
            for (int j = 0; j< cantNotas; j++) {
                if (datos[i][j] >= 4){
                    System.out.print(datos[i][j]+" ");
                }
            }
        }
        sumatotal = 0;
        mayor = promedios [0];
        menor = promedios [0];

        for (int i = 0; i < promedios.length; i++){
            sumatotal += promedios[i];
                
            if (promedios[i] > mayor){
                mayor = promedios[i];
            }       
            if (promedios[i] < menor){
                    menor = promedios[i];
            }
        }
        promediototal = sumatotal/promedios.length;

        System.out.println("\n\n\n PROMEDIO DEL CURSO");
        System.out.println("---------------------------------------");
        System.out.println("\nEl promedio del curso es: "+promediototal);
        
        
        
        System.out.println("\n-------------------------   ");
        System.out.print("        ");
        for (int i =0;i<cantNotas;i++){
            System.out.print("Nota"+(i+1) + "  ");
        }
        System.out.print("Promedio Mayor Menor\n");
      
        for (int i = 0; i < numAlum+3; i++){
            if (i<numAlum)
                System.out.print("Alumno "+(i+1)+" ");
                else if(i==numAlum)
                    System.out.print("Promedio ");
                    else if(i==numAlum+1)
                        System.out.print("Mayor    ");
                            else if (i==numAlum+2)
                                System.out.print("Menor    ");
                        
            
                for(int j =0;j<cantNotas+3;j++){
                    System.out.printf("%.2f   ", datos[i][j]);
                    
                    
                }System.out.print("\n");
        }
