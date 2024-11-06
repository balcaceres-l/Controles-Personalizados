Una vez descargado el archivo se importa el .JAR que esta en la carpeta DIST con los controles
Ejemplo básico de como agregar datos a la tabla, no es necesario crear un modelo, automaticamente se crea 

private void btnAgregarActionPerformed(java.awt.event.ActionEvent evt) {                                           
        String nombre = txtSoloLetras1.getText();
        String correo = txtCorreo1.getText();
        String numero = txtSoloNumeros1.getText();

        if (!nombre.isEmpty() && !correo.isEmpty() && !numero.isEmpty()) {

            Timer timer = new Timer(50, null);
            timer.addActionListener(e -> {
                int currentValue = progressCircle1.getValue();
                if (currentValue < 100) {
                    progressCircle1.setValue(currentValue + 1); // Incrementa el progreso
                } else {
                    timer.stop();

                    Vector<Object> rowData = new Vector<>();
                    rowData.add(nombre);
                    rowData.add(numero);
                    rowData.add(correo);
                    tablaCustom2.addRow(rowData);

                    txtSoloLetras1.setText("");
                    txtSoloNumeros1.setText("");
                    txtCorreo1.setText("");
                    progressCircle1.setValue(0);
                }
            });
            timer.start();
        } else {
            JOptionPane.showMessageDialog(this, "Por favor, llena todos los campos", "Campos incompletos", JOptionPane.WARNING_MESSAGE);
        }
    }  
