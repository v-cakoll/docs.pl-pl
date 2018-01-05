---
title: "Porady: czytanie ustawień w czasie wykonywania w języku C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85dc3a2c97b8fe5003c6026874dbdcaa9af89d77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Porady: czytanie ustawień w czasie wykonywania w języku C# #
W czasie wykonywania za pośrednictwem właściwości obiektu można odczytać ustawień zarówno zakresu aplikacji i zakresu użytkownika. Obiekt właściwości udostępnia wszystkie ustawienia domyślne dla projektu za pomocą elementu członkowskiego Properties.Settings.Default.  
  
### <a name="to-read-settings-at-run-time-with-c"></a>Aby odczytać ustawień w czasie wykonywania w języku C#  
  
-   Dostęp za pośrednictwem elementu członkowskiego Properties.Settings.Default odpowiednie ustawienia. Poniższy przykład przedstawia sposób przypisać ustawienie o nazwie `myColor` właściwości BackColor. Użytkownik musi mieć wcześniej utworzony plik ustawień zawierający ustawienie o nazwie `myColor` typu `System.Drawing.Color`. Aby uzyskać informacje dotyczące tworzenia pliku ustawień, zobacz [jak: utworzyć nowe ustawienie w czasie projektowania](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie ustawień aplikacji i ustawień użytkownika](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Instrukcje: pisanie ustawień użytkownika w czasie wykonywania w języku C#](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [Przegląd ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
