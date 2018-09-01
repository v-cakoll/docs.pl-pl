---
title: 'Instrukcje: Tworzenie klienta WCF (Windows Communication Foundation)'
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 9e6d75bf8911a3c36e63b3bc108faae823434d1d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397292"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Instrukcje: Tworzenie klienta WCF (Windows Communication Foundation)

Jest to czwarta sześciu zadań podrzędnych, wymagane do utworzenia aplikacji Windows Communication Foundation (WCF). Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.

W tym temacie opisano, jak można pobrać metadanych z usługi WCF i użyć go do utworzenia WCF serwera proxy, który można uzyskać dostęp do usługi. To zadanie zostało wykonane za pomocą funkcji Dodaj odwołanie do usługi udostępniane przez program Visual Studio. To narzędzie pobiera metadane z końcowego MEX usługi i generuje plik kodu źródłowego zarządzanego klienta proxy usługi w języka wybrane (C# domyślnie). Oprócz tworzenia serwera proxy klienta, narzędzie tworzy lub aktualizuje plik konfiguracji klienta, która pozwala połączyć się z usługą w jednej z jej punktów końcowych aplikacji klienckiej.

> [!NOTE]
> Można również użyć [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie do generowania klasy serwera proxy i konfiguracji zamiast Dodaj odwołanie do usługi w programie Visual Studio.

> [!WARNING]
> Podczas wywoływania usługi WCF z projekt biblioteki klas w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] funkcja Dodaj odwołanie do usługi służy do automatycznego generowania serwera proxy i skojarzony plik konfiguracji.  Plik konfiguracji nie będzie używany przez projekt biblioteki klas. Należy dodać ustawienia w pliku konfiguracyjnym wygenerowane do pliku app.config dla pliku wykonywalnego, który będzie wybierany biblioteki klas.

 Aplikacja kliencka używa klasy wygenerowany serwer proxy do komunikacji z usługą. Ta procedura jest opisana w [porady: używanie klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).

## <a name="to-create-a-windows-communication-foundation-client"></a>Można utworzyć klienta Windows Communication Foundation

1.  Utwórz nowy projekt aplikacji konsoli, klikając prawym przyciskiem myszy na wprowadzenie do rozwiązania, wybierając, **Dodaj**, **nowy projekt**. W **Dodaj nowy projekt** dialog w lewej części okna dialogowego wyboru **Windows** w obszarze **C#** lub **VB**. W górnej części okna dialogowego wybierz **aplikację Konsolową**. Nadaj projektowi nazwę `GettingStartedClient`.

2.  Ustaw docelową platformę projektu GettingStartedClient .NET Framework 4.5, klikając prawym przyciskiem myszy **GettingStartedClient** w Eksploratorze rozwiązań i wybierając polecenie **właściwości**. W polu listy rozwijanej etykietą **platformę docelową** wybierz **.NET Framework 4.5**. Platforma docelowa dla projektu VB jest nieco inne w oknie dialogowym właściwości projektu GettingStartedClient kliknij opcję **skompilować** karcie po lewej stronie ekranu, a następnie kliknij przycisk **zaawansowane Opcji kompilacji** przycisk w lewym dolnym rogu okna dialogowego. Następnie wybierz pozycję **.NET Framework 4.5** w polu listy rozwijanej etykietą **platformę docelową**.

     Ustawienie platforma docelowa spowoduje, że program Visual Studio 2011 ponowne załadowanie rozwiązania, naciśnij klawisz **OK** po wyświetleniu monitu.

3.  Dodaj odwołanie do System.ServiceModel do projektu GettingStartedClient, klikając prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedClient w Eksploratorze rozwiązań i wybierz pozycję **Dodaj** Odwołanie. W **Dodaj odwołanie** okna dialogowego wybierz **Framework** po lewej stronie okna dialogowego. W polu tekstowym wyszukiwania zestawów, wpisz `System.ServiceModel`. W górnej części okna dialogowego wybierz **System.ServiceModel**, kliknij przycisk **Dodaj** przycisk, a następnie kliknij przycisk **Zamknij** przycisku. Zapisz rozwiązania, klikając **Zapisz wszystko** znajdujący się poniżej menu głównego.

4.  Następnie dodasz odwołanie do usługi z usługą kalkulatora. Aby to zrobić, należy uruchomić aplikację konsoli GettingStartedHost. Gdy host jest uruchomiona, kliknij prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedClient w **Eksploratora rozwiązań** i wybierz **Dodaj**  >   **Dokumentacja usługi**. Wpisz następujący adres URL w polu adresu **Dodaj odwołanie do usługi** okna dialogowego: [ http://localhost:8000/ServiceModelSamples/Service ](http://localhost:8000/ServiceModelSamples/Service) i kliknij przycisk **Przejdź** przycisku. CalculatorService następnie powinna być wyświetlana w polu listy usług. Kliknij dwukrotnie CalculatorService i będzie on Rozwiń i Pokaż kontraktów usług implementowane przez usługę. Pozostaw domyślny obszar nazw i kliknij przycisk **OK** przycisku.

     Po dodaniu odwołania do usługi przy użyciu programu Visual Studio nowy element zostanie są wyświetlane w Eksploratorze rozwiązań, w obszarze folderu odwołania do usług w ramach projektu GettingStartedClient.  Jeśli używasz [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pliku kodu źródłowego i pliku app.config zostanie wygenerowany przez narzędzie.

     Można również użyć narzędzia wiersza polecenia [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) za pomocą odpowiednich przełączników, aby utworzyć kod klienta. Poniższy przykład generuje plik kodu i pliku konfiguracji usługi. Pierwszy przykład pokazuje, jak wygenerować serwera proxy w języku Visual Basic, a drugi pokazuje, jak wygenerowany serwer proxy w języku C#:

    ```
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service
    ```

    ```csharp
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service
    ```

 Utworzono serwer proxy, który aplikacja kliencka będzie używany do wywołania kalkulatora. Przejdź do następnego tematu w serii: [porady: Konfigurowanie klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a>Zobacz też

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)
- [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Instrukcje: używanie programu Svcutil.exe do pobierania dokumentów metadanych](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
