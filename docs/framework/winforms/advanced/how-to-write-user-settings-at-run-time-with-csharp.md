---
title: 'Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania w językuC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: a62bf540ebdc383f26bd4aed760b2562437047aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560947"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania w językuC# #
Ustawienia, które są w zakresie aplikacji są przeznaczone tylko do odczytu, a następnie można zmienić tylko w czasie projektowania lub przez zmianę w pliku config między sesjami aplikacji. Ustawienia, które są z zakresu użytkownika, jednak mogą być zapisywane w czasie wykonywania tak samo, jak należy zmienić dowolnej wartości właściwości. Nowa wartość będzie się powtarzać, czas trwania sesji aplikacji. Jednak można utrwalić zmiany ustawienia między sesjami aplikacji przez wywołanie metody zapisu.  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Instrukcje: Pisanie i utrwalanie ustawień użytkownika w czasie wykonywania za pomocąC#  
  
1.  Ustawienia dostępu i przypisz mu nową wartość, jak pokazano w poniższym przykładzie:  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  Jeśli chcesz utrwalić zmiany ustawienia między sesjami aplikacji, należy wywołać metodę zapisywania, jak pokazano w poniższym przykładzie:  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     Ustawienia użytkownika są zapisywane w pliku w podfolderze folderu lokalnego aplikacji ukryty przez użytkownika.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie ustawień aplikacji i ustawień użytkownika](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Instrukcje: Odczytaj ustawienia w czasie wykonywania za pomocąC#](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)
- [Przegląd ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
