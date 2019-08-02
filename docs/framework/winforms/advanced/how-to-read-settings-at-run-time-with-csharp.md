---
title: 'Instrukcje: Czytanie ustawień w czasie wykonywania w języku C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 6a40718d57fad4041eeea2fded03b7256abbe8d1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710223"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Instrukcje: Odczyt ustawień w czasie wykonywania przy użyciu języka C\#

W czasie wykonywania za pomocą obiektu Properties można odczytać zarówno ustawienia zakresu aplikacji, jak i zakresu użytkownika. Obiekt właściwości uwidacznia wszystkie ustawienia domyślne projektu za pośrednictwem właściwości. Settings. Default w domyślnej przestrzeni nazw projektu, w którym są zdefiniowane.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Aby odczytać ustawienia w czasie wykonywania przy użyciu języka C\#
  
Uzyskaj dostęp do odpowiedniego ustawienia za pośrednictwem właściwości. Settings. default. Poniższy przykład pokazuje, jak przypisać ustawienia o nazwie `myColor` do właściwości BackColor. Wymaga wcześniej utworzenia pliku ustawień zawierającego ustawienie o nazwie `myColor` typu. `System.Drawing.Color` Aby uzyskać informacje na temat tworzenia pliku ustawień, [zobacz How to: Utwórz nowe ustawienie w czasie](how-to-create-a-new-setting-at-design-time.md)projektowania.  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Zobacz także

- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania za pomocąC#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Przegląd ustawień aplikacji](application-settings-overview.md)
