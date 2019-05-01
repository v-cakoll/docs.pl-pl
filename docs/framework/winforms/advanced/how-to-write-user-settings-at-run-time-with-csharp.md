---
title: 'Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania w języku C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 264fa9706f9255d7324cad6d02c36cc424e28995
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778836"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Instrukcje: Pisanie ustawień użytkownika w czasie wykonywania w języku C\#

Ustawienia, które są w zakresie aplikacji są przeznaczone tylko do odczytu, a następnie można zmienić tylko w czasie projektowania lub przez zmianę w pliku config między sesjami aplikacji. Ustawienia, które są z zakresu użytkownika, jednak mogą być zapisywane w czasie wykonywania tak samo, jak należy zmienić dowolnej wartości właściwości. Nowa wartość będzie się powtarzać, czas trwania sesji aplikacji. Jednak można utrwalić zmiany ustawienia między sesjami aplikacji przez wywołanie metody zapisu.  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Instrukcje: Pisanie i utrwalanie ustawień użytkownika w czasie wykonywania przy użyciu języka C\#
  
1. Ustawienia dostępu i przypisz mu nową wartość, jak pokazano w poniższym przykładzie:  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. Jeśli chcesz utrwalić zmiany ustawienia między sesjami aplikacji, należy wywołać metodę zapisywania, jak pokazano w poniższym przykładzie:  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
Ustawienia użytkownika są zapisywane w pliku w podfolderze folderu lokalnego aplikacji ukryty przez użytkownika.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Instrukcje: Odczytaj ustawienia w czasie wykonywania za pomocąC#](how-to-read-settings-at-run-time-with-csharp.md)
- [Przegląd ustawień aplikacji](application-settings-overview.md)
