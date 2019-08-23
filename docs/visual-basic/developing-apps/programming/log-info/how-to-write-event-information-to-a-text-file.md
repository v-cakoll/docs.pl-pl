---
title: 'Instrukcje: Zapisz informacje o zdarzeniu w pliku tekstowym (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 4a34b57eb0a22dcf206456775cdd5817431292e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956825"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Instrukcje: Zapisz informacje o zdarzeniu w pliku tekstowym (Visual Basic)
Za pomocą `My.Application.Log` obiektów i `My.Log` można rejestrować informacje o zdarzeniach występujących w aplikacji. Ten przykład pokazuje, `My.Application.Log.WriteEntry` jak używać metody do rejestrowania informacji o śledzeniu w pliku dziennika.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Aby dodać i skonfigurować odbiornik dziennika plików  
  
1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.  
  
     \- lub —  
  
     Jeśli nie ma pliku App. config:  
  
    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.  
  
    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.  
  
    3. Kliknij przycisk **Dodaj**.  
  
2. `<listeners>` Znajdź sekcję w pliku konfiguracyjnym aplikacji.  
  
     W sekcji > \< \<źródłowej znajdują się > detektory z atrybutem Name "DefaultSource", który jest zagnieżdżony w sekcji System. Diagnostics >, która jest zagnieżdżona w obszarze najwyższego poziomu \< \<sekcja > konfiguracji.  
  
3. Dodaj ten element do tej `<listeners>` sekcji:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. Znajdź sekcję w sekcji zagnieżdżoną w sekcji najwyższego poziomu `<configuration>`. `<system.diagnostics>` `<sharedListeners>`  
  
5. Dodaj ten element do tej `<sharedListeners>` sekcji:  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Zmień wartość `customlocation` atrybutu na katalog dziennika.  
  
    > [!NOTE]
    > Aby ustawić wartość właściwości odbiornika, Użyj atrybutu, który ma taką samą nazwę jak właściwość, z wszystkimi literami w nazwie małymi literami. Na przykład `location` atrybuty <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> i `customlocation` ustawiają wartości właściwości i. <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A>  
  
### <a name="to-write-event-information-to-the-file-log"></a>Aby zapisać informacje o zdarzeniu w dzienniku plików  
  
- Użyj metody `My.Application.Log.WriteException` lub, aby zapisać informacje w dzienniku plików. `My.Application.Log.WriteEntry` Aby uzyskać więcej informacji, zobacz [jak: Zapisuj komunikaty](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) dziennika i [instrukcje: Wyjątki](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)dzienników.  
  
     Po skonfigurowaniu odbiornika dziennika plików dla zestawu otrzymuje on wszystkie komunikaty, które `My.Application.Log` zapisują z tego zestawu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: Wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
