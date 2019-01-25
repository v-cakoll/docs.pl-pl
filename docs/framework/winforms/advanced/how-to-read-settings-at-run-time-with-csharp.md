---
title: 'Instrukcje: Odczytaj ustawienia w czasie wykonywania za pomocąC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d798b40e5e337ea7652c8e82cb7fa860a87528b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521754"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Instrukcje: Odczytaj ustawienia w czasie wykonywania za pomocąC# #
W czasie wykonywania za pomocą obiektu właściwości można odczytać ustawień o zakresie aplikacji i zakresie użytkownika. Obiekt właściwości udostępnia wszystkie ustawienia domyślne dla projektu za pomocą elementu członkowskiego Properties.Settings.Default.  
  
### <a name="to-read-settings-at-run-time-with-c"></a>Do odczytywania ustawień w czasie wykonywania za pomocąC#  
  
-   Dostęp do odpowiedniego ustawienia za pomocą elementu członkowskiego Properties.Settings.Default. Poniższy przykład pokazuje, jak przypisać ustawienie o nazwie `myColor` właściwości BackColor. Musisz wcześniej utworzono plik ustawień zawierający ustawienia o nazwie `myColor` typu `System.Drawing.Color`. Aby uzyskać informacje dotyczące tworzenia pliku ustawień, zobacz [How to: Utwórz nowe ustawienie w czasie projektowania](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Używanie ustawień aplikacji i ustawień użytkownika](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania w językuC#](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)
- [Przegląd ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
