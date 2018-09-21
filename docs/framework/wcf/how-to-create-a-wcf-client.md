---
title: 'Instrukcje: Tworzenie klienta WCF (Windows Communication Foundation)'
ms.date: 09/14/2018
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 1eadb5008575a1a53d685db14d68e42d0dce1360
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478295"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Instrukcje: Tworzenie klienta WCF (Windows Communication Foundation)

Jest to czwarta sześciu zadań podrzędnych, wymagane do utworzenia aplikacji Windows Communication Foundation (WCF). Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.

W tym temacie opisano, jak można pobrać metadanych z usługi WCF i użyć go do utworzenia WCF serwera proxy, który można uzyskać dostęp do usługi. To zadanie jest wykonywane przy użyciu **Dodaj odwołanie do usługi** funkcje zapewniane przez program Visual Studio. To narzędzie pobiera metadane z końcowego MEX usługi i generuje plik kodu źródłowego zarządzanego klienta proxy usługi w języka wybrane (C# domyślnie). Oprócz tworzenia serwera proxy klienta, narzędzie tworzy lub aktualizuje plik konfiguracji klienta, która pozwala połączyć się z usługą w jednej z jej punktów końcowych aplikacji klienckiej.

> [!NOTE]
> Można również użyć [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie do generowania klasy serwera proxy i konfiguracji zamiast **Dodaj odwołanie do usługi** w programie Visual Studio.

> [!NOTE]
> Podczas wywoływania usługi WCF z projekt biblioteki klas w programie Visual Studio, możesz użyć **Dodaj odwołanie do usługi** funkcji w celu automatycznego generowania serwera proxy i skojarzony plik konfiguracji. Plik konfiguracji nie będzie używany przez projekt biblioteki klas. Należy dodać ustawienia w pliku konfiguracyjnym wygenerowane do pliku app.config dla pliku wykonywalnego, który wywołuje bibliotekę klas.

Aplikacja kliencka używa klasy wygenerowany serwer proxy do komunikacji z usługą. Ta procedura jest opisana w [porady: używanie klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).

## <a name="to-create-a-windows-communication-foundation-client"></a>Można utworzyć klienta Windows Communication Foundation

1. Utwórz nowy projekt aplikacji konsoli w programie Visual Studio. Kliknij prawym przyciskiem myszy, wprowadzenie do rozwiązania w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy projekt**. W **Dodaj nowy projekt** okna dialogowego po lewej stronie wybierz **pulpitu Windows** kategorię w obszarze **Visual C#** lub **języka Visual Basic**. Wybierz **Aplikacja konsoli (.NET Framework)** szablonu, a następnie nazwę projektu **GettingStartedClient**.

2. Dodaj odwołanie do System.ServiceModel do projektu GettingStartedClient. Kliknij prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedClient w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Dodaj odwołanie**. W **Dodaj odwołanie** okno dialogowe, wybierz opcję **Framework** po lewej stronie okna dialogowego, w obszarze **zestawy**. Znajdź i zaznacz **System.ServiceModel**, a następnie wybierz **OK**. Zapisz rozwiązanie, wybierając **pliku** > **Zapisz wszystko**.

3. Dodaj odwołanie do usługi z usługą kalkulatora.

   1. Najpierw należy uruchomić aplikację konsolową GettingStartedHost.

   2. Gdy host jest uruchomiona, kliknij prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedClient w **Eksploratora rozwiązań** i wybierz **Dodaj**  >   **Dokumentacja usługi**.

   3. Wprowadź następujący adres URL w polu adresu **Dodaj odwołanie do usługi** okno dialogowe: [http://localhost:8000/GettingStartedClient/Service](http://localhost:8000/GettingStartedClient/Service)

   4. Wybierz **Przejdź**.

   CalculatorService jest wyświetlany w **usług** pola listy. Kliknij dwukrotnie CalculatorService, aby go rozwinąć i wyświetlić kontraktów usług implementowane przez usługę. Pozostaw domyślny obszar nazw jako — to a wybierz **OK**.

    Podczas dodawania odwołania do usługi przy użyciu programu Visual Studio w pojawi się nowy element **Eksploratora rozwiązań** w obszarze **odwołania do usług** folderu w projekcie GettingStartedClient. Jeśli używasz [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) są generowane, narzędzia, plik kodu źródłowego i pliku app.config.

    Można również użyć narzędzia wiersza polecenia [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) za pomocą odpowiednich przełączników, aby utworzyć kod klienta. Poniższy przykład generuje plik kodu i pliku konfiguracji usługi. Pierwszy przykład pokazuje, jak wygenerować serwera proxy w języku Visual Basic, a drugi pokazuje, jak wygenerować serwera proxy w języku C#:

    ```shell
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

    ```shell
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

## <a name="next-steps"></a>Następne kroki

Utworzono serwer proxy, który aplikacja kliencka będzie używany do wywołania kalkulatora. Przejdź do następnego tematu w serii.

> [!div class="nextstepaction"]
> [Instrukcje: konfigurowanie klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a>Zobacz także

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)
- [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Instrukcje: używanie programu Svcutil.exe do pobierania dokumentów metadanych](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
