---
title: 'Porady: czytanie ustawień w czasie wykonywania w języku C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8259e2f429718793c01868855651d1000620fae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
