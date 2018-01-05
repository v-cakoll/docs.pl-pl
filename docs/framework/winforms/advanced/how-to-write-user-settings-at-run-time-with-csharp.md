---
title: "Porady: pisanie ustawień użytkownika w czasie wykonywania w języku C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 274a104d194c9db13d69d2024dc54595690c2ce3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Porady: pisanie ustawień użytkownika w czasie wykonywania w języku C# #
Ustawienia, które są zakresu aplikacji są tylko do odczytu, a można zmienić tylko w czasie projektowania lub przez zmodyfikowanie pliku .config między sesjami aplikacji. Ustawienia, które są zakresu użytkownika, jednak mogą być zapisywane w czasie wykonywania tak samo, jak można zmienić wartości właściwości. Nowa wartość będzie się powtarzać, w czasie trwania sesji aplikacji. Można ją utrwalić ustawienia między sesjami aplikacji przez wywołanie metody Zapisz zmiany.  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Porady: Pisanie i utrzymania ustawień użytkownika w czasie wykonywania w języku C#  
  
1.  Ustawienia dostępu i przypisz mu nową wartość, jak pokazano w poniższym przykładzie:  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  Jeśli chcesz utrwalić zmiany ustawienia między sesjami aplikacji, wywołaj metodę Save jak pokazano w poniższym przykładzie:  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     Ustawienia użytkownika są zapisywane w pliku w podfolderze folderu danych aplikacji lokalnej ukryty przez użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie ustawień aplikacji i ustawień użytkownika](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Instrukcje: czytanie ustawień w czasie wykonywania w języku C#](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [Przegląd ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
