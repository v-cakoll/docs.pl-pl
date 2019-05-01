---
title: 'Instrukcje: Zapisywanie informacji zdarzeniach w pliku tekstowym (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: e696ccb7327197c2f3a2468d30085dc6d390e034
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934335"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Instrukcje: Zapisywanie informacji zdarzeniach w pliku tekstowym (Visual Basic)
Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o zdarzeniach występujących w aplikacji. W tym przykładzie pokazano, jak używać `My.Application.Log.WriteEntry` metodę, aby rejestrować informacje śledzenia do pliku dziennika.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Aby dodać i skonfigurować odbiornika dziennika plików  
  
1. Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.  
  
     \- lub —  
  
     Jeśli nie ma żadnego pliku app.config:  
  
    1. Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2. Z **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.  
  
    3. Kliknij przycisk **Dodaj**.  
  
2. Znajdź `<listeners>` sekcji w pliku konfiguracyjnym aplikacji.  
  
     Znajdziesz \<odbiorników > sekcji \<źródło > sekcji atrybut name "DefaultSource", który jest zagnieżdżony w \<system.diagnostics > sekcji, która jest zagnieżdżony w najwyższegopoziomu\<konfiguracji > sekcji.  
  
3. Dodaj ten element, do którego `<listeners>` sekcji:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. Znajdź `<sharedListeners>` sekcji `<system.diagnostics>` sekcji zagnieżdżone najwyższego poziomu `<configuration>` sekcji.  
  
5. Dodaj ten element, do którego `<sharedListeners>` sekcji:  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Zmień wartość właściwości `customlocation` atrybutu do katalogu dziennika.  
  
    > [!NOTE]
    >  Aby ustawić wartość właściwości odbiornika, użyj atrybutu, który ma taką samą nazwę jak właściwości, za pomocą wszystkie znaki w małą nazwie. Na przykład `location` i `customlocation` atrybuty ustawione wartości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> i <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> właściwości.  
  
### <a name="to-write-event-information-to-the-file-log"></a>Można zapisać informacji o zdarzeniach do pliku dziennika  
  
- Użyj `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` metody, aby zapisać informacje o dzienniku plików. Aby uzyskać więcej informacji, zobacz [jak: Zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) i [jak: Rejestrowania wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Po skonfigurowaniu odbiornika plik dziennika dla zestawu, odbiera wszystkie komunikaty powodujące `My.Application.Log` zapisuje z tego zestawu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: Rejestruje wyjątki](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
