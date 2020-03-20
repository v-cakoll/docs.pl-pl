---
title: 'Samouczek: Tworzenie klienta programu Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184103"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Samouczek: Tworzenie klienta programu Windows Communication Foundation

W tym samouczku opisano czwarte z pięciu zadań wymaganych do utworzenia podstawowej aplikacji Programu Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Wprowadzenie do aplikacji Programu Windows Communication Foundation](getting-started-tutorial.md).

Następnym zadaniem tworzenia aplikacji WCF jest utworzenie klienta przez pobieranie metadanych z usługi WCF. Za pomocą programu Visual Studio, aby dodać odwołanie do usługi, która pobiera metadane z punktu końcowego MEX usługi. Visual Studio następnie generuje plik kodu źródłowego zarządzanego serwera proxy klienta w wybranym języku. Tworzy również plik konfiguracji klienta (*App.config*). Ten plik umożliwia aplikacji klienckiej połączyć się z usługą w punkcie końcowym.

> [!NOTE]
> Jeśli wywołujesz usługę WCF z projektu biblioteki klas w programie Visual Studio, użyj funkcji Dodaj odwołanie do **usługi,** aby automatycznie wygenerować serwer proxy i skojarzony plik konfiguracji. Ponieważ jednak projekty bibliotek klas nie używają tego pliku konfiguracyjnego, należy dodać ustawienia w wygenerowanym pliku konfiguracyjnym do pliku *App.config* dla pliku wykonywalnego, który wywołuje bibliotekę klas.

> [!NOTE]
> Alternatywnie użyj [narzędzia Narzędzia Metadata ServiceModel](#servicemodel-metadata-utility-tool) zamiast programu Visual Studio do wygenerowania klasy serwera proxy i pliku konfiguracji.

Aplikacja kliencka używa wygenerowanej klasy proxy do komunikowania się z usługą. Ta procedura jest [opisana w samouczku: Użyj klienta](how-to-use-a-wcf-client.md).

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie i konfigurowanie projektu aplikacji konsoli dla klienta WCF.
> - Dodaj odwołanie do usługi WCF do generowania klasy serwera proxy i plików konfiguracyjnych.

## <a name="create-a-windows-communication-foundation-client"></a>Tworzenie klienta programu Windows Communication Foundation

1. Tworzenie projektu aplikacji konsoli w programie Visual Studio:

    1. Z menu **Plik** wybierz polecenie **Otwórz** > **projekt/rozwiązanie** i przejdź do utworzonego wcześniej rozwiązania **GettingStarted** (*GettingStarted.sln*). Wybierz pozycję **Otwórz**.

    2. Z menu **Widok** wybierz pozycję **Eksplorator rozwiązań**.

    3. W oknie **Eksplorator rozwiązań** wybierz rozwiązanie GettingStarted (węzeł **górny),** a następnie z menu skrótów wybierz polecenie **Dodaj** > **nowy projekt.**

    4. W oknie **Dodaj nowy projekt** po lewej stronie wybierz kategorię Pulpit systemu **Windows** w obszarze **Visual C#** lub **Visual Basic**.

    5. Wybierz szablon **Aplikacji konsoli (.NET Framework)** i wprowadź *pozycję GettingStartedClient* dla **nazwy**. Kliknij przycisk **OK**.

2. Dodaj odwołanie w projekcie **GettingStartedClient** do <xref:System.ServiceModel> zestawu:

    1. W oknie **Eksplorator rozwiązań** wybierz folder **Odwołania** w obszarze projektu **GettingStartedClient,** a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów.

    2. W oknie **Dodaj odwołanie** w obszarze **Zestawy** po lewej stronie okna wybierz pozycję **Framework**.

    3. Znajdź i wybierz **system.ServiceModel**, a następnie wybierz przycisk **OK**.

    4. Zapisz rozwiązanie, wybierając **pozycję Zapisz** > **wszystkie**pliki .

3. Dodaj odwołanie do usługi kalkulatora:

   1. W oknie **Eksplorator rozwiązań** wybierz folder **Odwołania** w ramach projektu **GettingStartedClient,** a następnie wybierz polecenie **Dodaj odwołanie do usługi** z menu skrótów.

   2. W oknie **Dodawanie odwołania do usługi** wybierz pozycję **Odnajduj**.

      Uruchomi się usługa CalculatorService, a program Visual Studio wyświetli ją w polu **Usługi.**

   3. Wybierz **CalculatorService,** aby ją rozwinąć i wyświetlić umowy serwisowe zaimplementowane przez usługę. Pozostaw domyślny **obszar nazw** i wybierz przycisk **OK**.

      Program Visual Studio dodaje nowy element w folderze **Połączone usługi** w projekcie **GettingStartedClient.**

### <a name="servicemodel-metadata-utility-tool"></a>Narzędzie narzędzia Metadata usługi ServiceModel

Poniższe przykłady pokazują, jak opcjonalnie użyć [narzędzia ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania pliku klasy proxy. To narzędzie generuje plik klasy proxy i plik *App.config.* Poniższe przykłady pokazują, jak wygenerować serwer proxy w języku C# i Visual Basic, odpowiednio:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Plik konfiguracji klienta

Po utworzeniu klienta program Visual Studio tworzy plik konfiguracyjny **App.config** w projekcie **GettingStartedClient,** który powinien być podobny do następującego przykładu:

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

W sekcji [ \<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) zwróć uwagę na [ \<punkt końcowy>](../configure-apps/file-schema/wcf/endpoint-element.md) element. Element ** &lt;punktu&gt; końcowego** definiuje punkt końcowy, który klient używa do uzyskania dostępu do usługi w następujący sposób:

- Adres: `http://localhost:8000/GettingStarted/CalculatorService`. Adres punktu końcowego.
- Umowa serwisowa: `ServiceReference1.ICalculator`. Umowa serwisowa obsługuje komunikację między klientem WCF a usługą. Visual Studio wygenerował ten kontrakt, gdy był używany jego Dodaj funkcję **odwołania do usługi.** Zasadniczo jest to kopia umowy zdefiniowanej w projekcie GettingStartedLib.
- Wiązanie: <xref:System.ServiceModel.WSHttpBinding>. Powiązanie określa HTTP jako transport, interoperacyjne zabezpieczenia i inne szczegóły konfiguracji.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie i konfigurowanie projektu aplikacji konsoli dla klienta WCF.
> - Dodaj odwołanie do usługi WCF do generowania plików klasy proxy i konfiguracji dla aplikacji klienckiej.

Przejdź do następnego samouczka, aby dowiedzieć się, jak korzystać z wygenerowanego klienta.

> [!div class="nextstepaction"]
> [Samouczek: Korzystanie z klienta WCF](how-to-use-a-wcf-client.md)
