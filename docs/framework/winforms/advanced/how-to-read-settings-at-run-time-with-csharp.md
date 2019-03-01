---
title: 'Instrukcje: Odczytaj ustawienia w czasie wykonywania za pomocąC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8cdc1a79f1ab327ae037cd6a04aa769196405127
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974851"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Instrukcje: Odczytaj ustawienia w czasie wykonywania przy użyciu języka C\#

W czasie wykonywania za pomocą obiektu właściwości można odczytać ustawień o zakresie aplikacji i zakresie użytkownika. Obiekt właściwości udostępnia wszystkie ustawienia domyślne dla projektu za pomocą elementu członkowskiego Properties.Settings.Default.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Do odczytywania ustawień w czasie wykonywania przy użyciu języka C\#
  
Dostęp do odpowiedniego ustawienia za pomocą elementu członkowskiego Properties.Settings.Default. Poniższy przykład pokazuje, jak przypisać ustawienie o nazwie `myColor` właściwości BackColor. Musisz wcześniej utworzono plik ustawień zawierający ustawienia o nazwie `myColor` typu `System.Drawing.Color`. Aby uzyskać informacje dotyczące tworzenia pliku ustawień, zobacz [How to: Utwórz nowe ustawienie w czasie projektowania](how-to-create-a-new-setting-at-design-time.md).  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Zobacz także

- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania w językuC#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Przegląd ustawień aplikacji](application-settings-overview.md)
