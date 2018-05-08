---
title: Narzędzia dostawcy odwołanie z usługą sieci Web Microsoft WCF
description: Przegląd Microsoft WCF sieci Web usługi odwołanie dostawca narzędzia, która dodaje funkcjonalność platformy .NET Core i ASP.NET Core projektów, podobnie jak Dodaj odwołanie do usługi .NET Framework projektów.
author: mlacouture
ms.author: johalex
ms.date: 04/19/2018
ms.custom: mvc
ms.openlocfilehash: 416ca4dbedcf6e610aa5307c87934c0cb18be749
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="microsoft-wcf-web-service-reference-provider-tool"></a>Narzędzia dostawcy odwołanie z usługą sieci Web Microsoft WCF

W ciągu lat wielu deweloperów programu Visual Studio korzystali produktywność który [ **Dodaj odwołanie do usługi** ](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) Narzędzie dostarczone w razie potrzeby projektów .NET Framework dostępu do usług sieci web.  **Odwołania do usługi sieci Web WCF** narzędzie to rozszerzenie usługi Visual Studio połączone, które udostępnia środowisko będąca odpowiednikiem Dodaj odwołanie do usługi .NET Core i ASP.NET Core projektów. To narzędzie pobiera metadane z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej, lub z pliku WSDL i generuje plik zgodnego źródła .NET Core zawierające kod serwera proxy klienta usługi Windows Communication Foundation (WCF) używanego do dostępu do sieci web Usługa.

> [!IMPORTANT]
> Użytkownik powinien odwoływać się tylko usługi z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo. 

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 w 15,5 cala](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) lub nowszy

## <a name="how-to-use-the-extension"></a>Jak używać rozszerzenia

> [!NOTE]
> **Odwołania do usługi sieci Web WCF** opcja ma zastosowanie do projektów utworzonych za pomocą następujących szablonów projektu:
> * **Visual C#** > **.NET Core**
> * **Visual C#** > **.NET Standard**
> * **Visual C#** > **Web** > **aplikacji sieci Web platformy ASP.NET Core**

Przy użyciu **aplikacji sieci Web platformy ASP.NET Core** szablon projektu, na przykład, w tym artykule przedstawiono dodawanie odwołania do usługi WCF do projektu:

1. W Eksploratorze rozwiązań kliknij dwukrotnie **usług połączonych** węzła projektu (dla projektu platformy .NET Core lub .NET Standard ta opcja jest dostępna po kliknięciu prawym przyciskiem myszy na **zależności** węzła Projekt w Eksploratorze rozwiązań).

**Usług połączonych** zostanie wyświetlona strona, jak pokazano na poniższej ilustracji:

![Karta podłączonej usługi](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Na **usług połączonych** kliknij przycisk **dostawcy odwołania dla usług sieci Web firmy Microsoft WCF**. Spowoduje to wyświetlenie **skonfigurować odwołania usługi sieci Web WCF** kreatora:

![Karta punktu końcowego usługi](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Wybierz usługę.

    3a. Dostępnych jest kilka opcji wyszukiwania usług dostępnych w ramach **skonfigurować odwołania usługi sieci Web WCF** kreatora:
    
     * Aby wyszukać usługi zdefiniowane w bieżącym rozwiązaniu, kliknij przycisk **odnajdowania** przycisku. 
     * Aby wyszukać usług hostowanych pod określonym adresem, wprowadź adres URL usługi, w **adres** polu i kliknij przycisk **Przejdź** przycisku.
     * Aby wybrać plik WSDL, który zawiera informacje o metadanych dla usługi sieci web, kliknij przycisk **Przeglądaj** przycisku. 
     
    3b. Wybierz usługę z listy wyników wyszukiwania w **usług** pole. W razie potrzeby wprowadź przestrzeń nazw dla wygenerowanego kodu w odpowiednich **Namespace** pola tekstowego.
    
    3c. Kliknij przycisk **dalej** przycisk, aby otworzyć **opcje typu danych** i **opcje klienta** stron. Alternatywnie kliknij **Zakończ** przycisk, aby użyć domyślnych opcji.


4. **Opcje typu danych** formularza pozwala dostosować ustawienia konfiguracji usługi wygenerowanego odwołania:

![Karta Opcje typu danych](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

> [!NOTE]
> **Ponownie użyj typów w przywoływanych zestawach** pola wyboru jest przydatne, gdy typy danych potrzebne do generowania kodu odwołania usługi są zdefiniowane w jednym z zestawów występujących w odwołaniach projektu.  Należy ponownie wykorzystać te istniejących typów danych, aby uniknąć problemów z konflikt lub środowisko uruchomieniowe typu kompilacji.

Może wystąpić opóźnienie, gdy informacje o typie został załadowany, w zależności od liczby zależności projektu i inne czynniki wydajności systemu. **Zakończ** przycisk jest niedostępny podczas ładowania, chyba że **ponownie użyj typów w przywoływanych zestawach** pole wyboru jest zaznaczone.

5. Kliknij przycisk **Zakończ** gdy wszystko będzie gotowe.


Podczas wyświetlania postępu, narzędzie:

* Pobiera metadane z usługi WCF. 
* Generuje kod odwołania usługi w pliku o nazwie *reference.cs*i dodaje go do projektu pod **usług połączonych** węzła. 
* Aktualizuje plik projektu (.csproj) odwołania do pakietu NuGet wymagane, aby skompilować i uruchomić na platformie docelowej.

![Okno postępu](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Po ukończeniu tych procesów, można utworzyć wystąpienia typu wygenerowanego klienta WCF i wywołania operacji usługi.

## <a name="next-steps"></a>Następne kroki

### <a name="feedback--questions"></a>Opinie i pytania
Jeśli masz pytania lub opinie, [Otwórz problemu w serwisie GitHub](https://github.com/dotnet/wcf/issues/new). Można także przejrzeć wszystkie istniejące pytania lub problemy [w repozytorium usługi WCF w usłudze GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Uwagi do wersji
* Zapoznaj się [informacje o wersji](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) uzyskać informacje o zaktualizowanej wersji, w tym znanych problemów. 
