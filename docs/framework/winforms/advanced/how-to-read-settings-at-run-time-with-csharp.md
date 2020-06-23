---
title: 'Porady: czytanie ustawień w czasie wykonywania w języku C#'
description: Informacje o sposobie odczytywania ustawień zakresu aplikacji i zakresu użytkownika w czasie wykonywania w języku C# za pomocą obiektu Properties.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d784544e018bb693c501e35ea36fcae1946ef5eb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903357"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Instrukcje: odczytywanie ustawień w czasie wykonywania przy użyciu języka C\#

W czasie wykonywania za pomocą obiektu Properties można odczytać zarówno ustawienia zakresu aplikacji, jak i zakresu użytkownika. Obiekt właściwości uwidacznia wszystkie ustawienia domyślne projektu za pośrednictwem właściwości. Settings. Default w domyślnej przestrzeni nazw projektu, w którym są zdefiniowane.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Aby odczytać ustawienia w czasie wykonywania przy użyciu języka C\#
  
Uzyskaj dostęp do odpowiedniego ustawienia za pośrednictwem właściwości. Settings. default. Poniższy przykład pokazuje, jak przypisać ustawienia o nazwie `myColor` do właściwości BackColor. Wymaga wcześniej utworzenia pliku ustawień zawierającego ustawienie o nazwie `myColor` typu `System.Drawing.Color` . Aby uzyskać informacje na temat tworzenia pliku ustawień, zobacz [How to: Create a New Setting in Time Design](how-to-create-a-new-setting-at-design-time.md).  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Zobacz też

- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Instrukcje: pisanie ustawień użytkownika w czasie wykonywania w języku C#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Przegląd ustawień aplikacji](application-settings-overview.md)
