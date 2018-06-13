---
title: 'Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 3adb594ee42b7b1fad77a54af04bb9f37f30c19a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589061"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)
Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji. Ten przykład przedstawia sposób użycia `My.Application.Log.WriteEntry` metody do rejestrowania informacji śledzenia w pliku dziennika.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Aby dodać i skonfigurować odbiornik pliku dziennika  
  
1.  Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.  
  
     \- lub -  
  
     Jeśli plik app.config, nie istnieje:  
  
    1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2.  Z **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.  
  
    3.  Kliknij przycisk **Dodaj**.  
  
2.  Zlokalizuj `<listeners>` sekcji w pliku konfiguracyjnym aplikacji.  
  
     Można znaleźć \<odbiorników > w sekcji \<źródło > sekcji, atrybut name "DefaultSource", która jest zagnieżdżona w obszarze \<system.diagnostics > sekcji, która jest zagnieżdżona w obszarze najwyższegopoziomu\<konfiguracji > sekcji.  
  
3.  Dodaj ten element, do którego `<listeners>` sekcji:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4.  Zlokalizuj `<sharedListeners>` sekcji `<system.diagnostics>` sekcji zagnieżdżone najwyższego poziomu `<configuration>` sekcji.  
  
5.  Dodaj ten element, do którego `<sharedListeners>` sekcji:  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Zmień wartość `customlocation` atrybutu do katalogu dziennika.  
  
    > [!NOTE]
    >  Aby ustawić wartość właściwości odbiornika, użyj atrybut, który ma taką samą nazwę jak właściwości, w których wszystkie litery w małych nazwy. Na przykład `location` i `customlocation` atrybuty ustawione wartości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> i <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> właściwości.  
  
### <a name="to-write-event-information-to-the-file-log"></a>Można zapisać informacji o zdarzeniach w pliku dziennika  
  
-   Użyj `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` metody, aby zapisać informacje o pliku dziennika. Aby uzyskać więcej informacji, zobacz [jak: zapisu komunikaty dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) i [porady: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Po skonfigurowaniu odbiornika plik dziennika dla zestawu odbiera wszystkie wiadomości, które `My.Application.Log` zapisuje z tego zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Instrukcje: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
