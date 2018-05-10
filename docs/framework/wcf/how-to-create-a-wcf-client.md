---
title: 'Instrukcje: Tworzenie klienta WCF (Windows Communication Foundation)'
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d2932293536f875d8986d8d49842cddc196ced0f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Instrukcje: Tworzenie klienta WCF (Windows Communication Foundation)
Jest to czwarty sześciu zadania wymagane do utworzenia aplikacji Windows Communication Foundation (WCF). Omówienie sześciu wszystkich zadań, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.  
  
 W tym temacie opisano, jak pobrać metadanych z usługą WCF i użyć go do tworzenia usług WCF serwer proxy, który można uzyskać dostępu do usługi. To zadanie zostało wykonane przy użyciu funkcji Dodaj odwołanie do usługi udostępniane przez program Visual Studio. To narzędzie pobiera metadane z punktu końcowego MEX usługi i generuje plik kodu zarządzanego źródła dla klienta serwera proxy w języku wybrano (C# domyślnie). Oprócz tworzenia serwera proxy klienta, narzędzie tworzy lub aktualizuje plik konfiguracji klienta, który umożliwia aplikacjom klienta połączyć się z usługą w jednej z jego punktów końcowych.  
  
> [!NOTE]
>  Można również użyć [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie do generowania klasy serwera proxy i konfiguracji zamiast Dodaj odwołanie do usługi w programie Visual Studio.  
  
> [!WARNING]
>  Podczas wywoływania usługi WCF z projektu biblioteki klas w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] funkcja Dodaj odwołanie do usługi umożliwia automatyczne generowanie serwera proxy i skojarzony plik konfiguracji.  Plik konfiguracji nie będzie służyć za projektu biblioteki klas. Należy dodać ustawienia w pliku konfiguracyjnym wygenerowanego pliku app.config dla pliku wykonywalnego, który będzie dzwonić, biblioteki klas.  
  
 Aplikacja kliencka używa klasy wygenerowany serwer proxy do komunikacji z usługą. Ta procedura jest opisana w [porady: używanie klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
### <a name="to-create-a-windows-communication-foundation-client"></a>Aby utworzyć klienta Windows Communication Foundation  
  
1.  Utwórz nowy projekt aplikacji konsoli, klikając prawym przyciskiem myszy na wprowadzenie rozwiązanie, jeśli zostanie wybrana, **Dodaj**, **nowy projekt**. W **Dodawanie nowego projektu** dialog w lewej strony okna dialogowego wyboru **Windows** w obszarze **C#** lub **VB**. W górnej części okna dialogowego wybierz **aplikacji konsoli**. Nazwij projekt `GettingStartedClient`.  
  
2.  Ustaw docelową platformę projektu GettingStartedClient .NET Framework 4.5, klikając prawym przyciskiem myszy **GettingStartedClient** w Eksploratorze rozwiązań i wybierając **właściwości**. W polu listy rozwijanej etykietą **platformy docelowej** wybierz **.NET Framework 4.5**. Ustawienie platformy docelowej dla projektu VB różni się nieco, w oknie dialogowym właściwości projektu GettingStartedClient, kliknij przycisk **skompilować** po lewej stronie ekranu, a następnie kliknij pozycję **zaawansowane Opcje kompilacji** przycisk w lewym dolnym rogu okna dialogowego. Następnie wybierz **.NET Framework 4.5** w polu listy rozwijanej etykietą **platformy docelowej**.  
  
     Ustawienie platformy docelowej spowoduje programu Visual Studio 2011 ponowne załadowanie rozwiązania, naciśnij klawisz **OK** po wyświetleniu monitu.  
  
3.  Dodaj odwołanie do System.ServiceModel do projektu GettingStartedClient, klikając prawym przyciskiem myszy **odwołania** GettingStartedClient projekt w Eksploratorze rozwiązań i wybierz folder **Dodaj** Odwołanie. W **Dodaj odwołanie** oknie dialogowym wybierz pozycję **Framework** po lewej stronie okna dialogowego. W polu tekstowym wyszukiwania zestawów, wpisz w `System.ServiceModel`. W górnej części okna dialogowego wybierz **System.ServiceModel**, kliknij przycisk **Dodaj** przycisk **Zamknij** przycisku. Zapisz rozwiązanie, klikając **Zapisz wszystko** znajdujący się pod menu głównego.  
  
4.  Dalej można wlll dodać odwołania do usługi z usługą Kalkulator. Zanim można to zrobić, należy uruchomić GettingStartedHost aplikacji konsoli. Po uruchomieniu hosta można kliknij prawym przyciskiem myszy folder odwołań w projekcie GettingStartedClient w Eksploratorze rozwiązań i wybierz opcję Dodaj odwołanie do usługi i wpisz następujący adres URL w polu adres okna dialogowego Dodaj odwołanie do usługi: HYPERLINK "http://localhost:8000/ServiceModelSamples/Service" http://localhost:8000/ServiceModelSamples/Service i kliknij przycisk **Przejdź** przycisku. CalculatorService następnie powinna być wyświetlana w polu listy usług, kliknij dwukrotnie CalculatorService i zostanie rozwinąć i wyświetlić kontraktów usług zaimplementowanych przez usługę. Pozostaw domyślny obszar nazw i kliknij przycisk **OK** przycisku.  
  
     Po dodaniu się, że odwołanie do usługi przy użyciu programu Visual Studio nowy element pojawi się w Eksploratorze rozwiązań w folderze usługi odwołań w projekcie GettingStartedClient.  Jeśli używasz [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia można wygenerować pliku kodu źródłowego i pliku app.config.  
  
     Można także użyć narzędzia wiersza polecenia [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z odpowiednich przełączników, aby utworzyć kodu klienta. Poniższy przykład umożliwia wygenerowanie pliku kodu i pliku konfiguracji dla usługi. Pierwszym przykładzie pokazano, jak Generowanie serwera proxy w języku VB, a drugi przedstawia sposób wygenerowany serwer proxy w języku C#:  
  
    ```  
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
    ```csharp  
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
 Serwer proxy, który aplikacja kliencka będzie używany do wywołania tej usługi Kalkulator została utworzona. Przejdź do następnego tematu w serii: [porady: Konfigurowanie klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)  
 [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Instrukcje: używanie programu Svcutil.exe do pobierania dokumentów metadanych](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
