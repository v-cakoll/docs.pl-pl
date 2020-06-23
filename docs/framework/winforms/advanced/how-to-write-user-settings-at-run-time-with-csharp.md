---
title: 'Porady: pisanie ustawień użytkownika w czasie wykonywania w języku C#'
description: Informacje o sposobie pisania ustawień w czasie wykonywania w języku C# poprzez Utrwalanie zmian ustawień między sesjami aplikacji przez wywołanie metody Save.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 6154ff1b92d6c2d4c788299e59eb8f73e6b69c4b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904328"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Instrukcje: pisanie ustawień użytkownika w czasie wykonywania przy użyciu języka C\#

Ustawienia, które są objęte zakresem aplikacji, są tylko do odczytu i mogą być zmieniane tylko w czasie projektowania lub przez zmianę pliku. config między sesjami aplikacji. Ustawienia, które są objęte zakresem użytkownika, można jednak zapisywać w czasie wykonywania tak samo jak w przypadku zmiany dowolnej wartości właściwości. Nowa wartość będzie trwała w czasie trwania sesji aplikacji. Zmiany ustawień między sesjami aplikacji można zachować, wywołując metodę Save.  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Instrukcje: zapisywanie i utrwalanie ustawień użytkownika w czasie wykonywania przy użyciu języka C\#
  
1. Uzyskaj dostęp do tego ustawienia i przypisz go nową wartość, jak pokazano w tym przykładzie:  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. Jeśli chcesz zachować zmiany ustawień między sesjami aplikacji, wywołaj metodę Save, jak pokazano w tym przykładzie:  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
Ustawienia użytkownika są zapisywane w pliku w podfolderze w lokalnym ukrytym folderze dane aplikacji użytkownika.  
  
## <a name="see-also"></a>Zobacz też

- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Porady: czytanie ustawień w czasie wykonywania w języku C#](how-to-read-settings-at-run-time-with-csharp.md)
- [Przegląd ustawień aplikacji](application-settings-overview.md)
