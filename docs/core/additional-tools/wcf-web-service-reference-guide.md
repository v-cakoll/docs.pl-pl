---
title: Dodawanie odwołania do usługi sieci Web WCF
description: Omówienie narzędzia dostawcy usług sieci Web Microsoft WCF, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobne do dodawania dokumentacji usługi dla projektów .NET Framework.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc
ms.openlocfilehash: cdd6b457d289dd7b752c97c5645f0797f24b72aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715685"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>Korzystanie z narzędzia Dostawcy informacji o usługach sieci Web WCF

Z biegiem lat wielu deweloperów programu Visual Studio cieszyło się produktywnością, jaką narzędzie [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) zapewniało, gdy ich projekty .NET Framework były potrzebne do uzyskania dostępu do usług sieci web.  Narzędzie **WCF Web Service Reference** to rozszerzenie usługi połączonej z programami Visual Studio, które zapewnia środowisko, takie jak funkcja Dodaj odwołanie do usługi .NET Core i ASP.NET core. To narzędzie pobiera metadane z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub z pliku WSDL i generuje plik źródłowy zgodny z .NET Core zawierający kod proxy klienta Windows Communication Foundation (WCF), za pomocą którego można uzyskać dostęp do sieci Web Usługi.

> [!IMPORTANT]
> Należy odwoływać się tylko do usług z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) lub nowszej

## <a name="how-to-use-the-extension"></a>Jak korzystać z rozszerzenia

> [!NOTE]
> Opcja **Odwołanie do usługi sieci Web WCF** ma zastosowanie do projektów utworzonych przy użyciu następujących szablonów projektów:
>
> - **Visual C#** > **.NET Core**
> - **Visual C#** > **.NET Standard**
> - **Wizualna aplikacja** > sieci Web ASP.NET**sieci Web** > języka**C#**

Korzystając z szablonu projektu **ASP.NET Core Web Application** jako przykład, w tym artykule przeprowadzi Cię przez dodanie odwołania usługi WCF do projektu:

1. W Eksploratorze rozwiązań kliknij dwukrotnie węzeł **Połączonych usług** projektu (dla projektu .NET Core lub .NET Standard ta opcja jest dostępna po kliknięciu prawym przyciskiem myszy węzła **Zależności** projektu w Eksploratorze rozwiązań).

    Strona **Połączone usługi** jest wyświetlana w sposób pokazany na poniższej ilustracji:

    ![Karta Połączone usługi Visual Studio dla programu .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Na stronie **Połączone usługi** kliknij pozycję **Dostawca dokumentacji usługi sieci Web firmy Microsoft WCF**. Spowoduje to **wyświetlenie kreatora Konfigurowanie usługi sieci Web WCF:**

    ![Karta Punkt końcowy usługi Visual Studio dla programu .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Wybierz usługę.

    3a. Istnieje kilka opcji wyszukiwania usług dostępnych w kreatorze **Konfigurowanie odwołania do usługi sieci Web WCF:**

     * Aby wyszukać usługi zdefiniowane w bieżącym rozwiązaniu, kliknij przycisk **Odnajtzej.**
     * Aby wyszukać usługi hostowane pod określonym adresem, wprowadź adres URL usługi w polu **Adres** i kliknij przycisk **Przejdź.**
     * Aby wybrać plik WSDL zawierający informacje o metadanych usługi sieci Web, kliknij przycisk **Przeglądaj.**

    3b. Wybierz usługę z listy wyników wyszukiwania w polu **Usługi.** W razie potrzeby wprowadź obszar nazw wygenerowanego kodu w odpowiednim polu tekstowym **Obszar nazw.**

    3c. Kliknij przycisk **Dalej,** aby otworzyć **strony Opcje typu danych** i Opcje **klienta.** Alternatywnie kliknij przycisk **Zakończ,** aby użyć opcji domyślnych.

4. Formularz **Opcje typu danych** umożliwia zawężenie wygenerowanych ustawień konfiguracji odwołania do usługi:

    ![Karta Opcje typu danych programu Visual Studio dla programu .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > Opcja pola wyboru **Ponowne użycie w zestawach, do których istnieje odwołanie,** jest przydatna, gdy typy danych potrzebne do generowania kodu referencyjnego usługi są zdefiniowane w jednym z zestawów, do których odwołuje się projekt.  Ważne jest, aby ponownie użyć tych istniejących typów danych, aby uniknąć kolizji typu kompilacji lub problemy ze środowiska uruchomieniowego.

    Może wystąpić opóźnienie podczas ładowania informacji o typie, w zależności od liczby zależności projektu i innych czynników wydajności systemu. Przycisk **Zakończ** jest wyłączony podczas ładowania, chyba że pole wyboru **Ponowne użycie w zestawach, do których istnieje** odwołanie, nie jest zaznaczone.

5. Po zakończeniu kliknij **przycisk Zakończ.**

Podczas wyświetlania postępu, narzędzie:

- Pobiera metadane z usługi WCF.
- Generuje kod odwołania do usługi w pliku o nazwie *reference.cs*i dodaje go do projektu w węźle **Połączone usługi.**
- Aktualizuje plik projektu (csproj) z odwołaniami do pakietu NuGet wymaganymi do kompilacji i uruchamiania na platformie docelowej.

![Okno Postępu programu Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Po zakończeniu tych procesów można utworzyć wystąpienie wygenerowanego typu klienta WCF i wywołać operacje usługi.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do aplikacji Windows Communication Foundation](../../framework/wcf/getting-started-tutorial.md)
- [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [Obsługiwane przez WCF funkcje programu .NET Core](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a>Opinie & pytania

Jeśli masz jakiekolwiek pytania lub opinie, zgłoś to w [społeczności deweloperów](https://developercommunity.visualstudio.com/) za pomocą narzędzia [Zgłoś problem.](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)

## <a name="release-notes"></a>Informacje o wersji

- Informacje o [wydaniu można znaleźć](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) w informacjach o wydaniu, w tym znanych problemach.
