---
title: Dodaj odwołanie do usługi sieci Web WCF
description: Przegląd Microsoft WCF Web Service Reference Provider narzędzie które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobne do Dodaj odwołanie do usługi dla projektów programu .NET Framework.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 806f6e90aedc669c3a56ce1cde64311bdd4af32c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750494"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>Użyj narzędzia dostawcy odwołanie do usługi sieci Web WCF

W ciągu lat wielu deweloperów programu Visual Studio są Państwo zadowoleni produktywność, [ **Dodaj odwołanie do usługi** ](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) narzędzia podane w razie ich projektów programu .NET Framework na dostęp do usług sieci web.  **WCF Web Service Reference** narzędzie to rozszerzenie usług połączonych programu Visual Studio, które zapewnia środowisko, takich jak funkcja Dodaj odwołanie do usługi .NET Core i ASP.NET Core projektów. To narzędzie służy do pobierania metadanych z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub z pliku WSDL i generuje plik zgodne źródło .NET Core, zawierające kod serwera proxy klienta Windows Communication Foundation (WCF), który służy do dostępu do sieci web Usługa.

> [!IMPORTANT]
> Użytkownik powinien odwoływać się tylko do usług z zaufanego źródła. Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) lub nowsze wersje

## <a name="how-to-use-the-extension"></a>Jak używać rozszerzenia

> [!NOTE]
> **WCF Web Service Reference** opcja ma zastosowanie do projektów utworzonych za pomocą następujące szablony projektów:
> * **Visual C#** > **.NET Core**
> * **Wizualne C#**   >  **.NET Standard**
> * **Wizualne C#**   >  **Web** > **aplikacji sieci Web platformy ASP.NET Core**

Za pomocą **aplikacji sieci Web programu ASP.NET Core** szablon projektu, na przykład, ten artykuł przeprowadzi Cię przez dodawanie odwołania do usługi WCF do projektu:

1. W Eksploratorze rozwiązań kliknij dwukrotnie **podłączone usługi** węzła projektu (dla projektu .NET Core lub .NET Standard ta opcja jest dostępna po kliknięciu prawym przyciskiem myszy **zależności** węzła Projekt w Eksploratorze rozwiązań).

    **Podłączone usługi** zostanie wyświetlona strona, jak pokazano na poniższej ilustracji:

    ![Wizualne kartę podłączone usługi Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Na **podłączone usługi** kliknij **Microsoft WCF Web Service Reference Provider**. Spowoduje to przejście **skonfigurować WCF Web Service Reference** kreatora:

    ![Wizualne kartę punktu końcowego usługi Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Wybierz usługę.

    3a. Kilka innych opcji wyszukiwania usługi są dostępne w ramach **skonfigurować WCF Web Service Reference** kreatora:

     * Aby wyszukać usługi zdefiniowane w bieżącym rozwiązaniu, kliknij przycisk **odnajdź** przycisku.
     * Aby wyszukać usług hostowanych pod określonym adresem, wprowadź adres URL usługi, w **adres** pole, a następnie kliknij przycisk **Przejdź** przycisku.
     * Aby wybrać plik WSDL, który zawiera informacje o metadanych dla usługi sieci web, kliknij przycisk **Przeglądaj** przycisku.

    3b. Wybierz usługę z listy wyników wyszukiwania w **usług** pole. W razie potrzeby wprowadź przestrzeń nazw dla wygenerowanego kodu w odpowiednich **Namespace** pola tekstowego.

    3c. Kliknij przycisk **dalej** przycisk, aby otworzyć **opcje typu danych** i **opcje klienta** stron. Alternatywnie kliknij **Zakończ** przycisk, aby użyć opcji domyślnych.

4. **Opcje typu danych** formularz pozwala dostosować ustawienia konfiguracji odniesienia wygenerowanego usługi:

    ![Visual Studio danych typu karta Opcje dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > **Ponownie użyj typów w przywoływanych zestawach** pole wyboru opcji jest przydatne w przypadku, gdy typy danych służące do generowania kodu odwołania usługi są definiowane w jeden z przywoływanych zestawach projektu.  Należy ponownie użyć tych istniejących typów danych, aby uniknąć problemów z konflikt lub środowisko uruchomieniowe typów w czasie kompilacji.

    Może wystąpić opóźnienie, podczas ładowania informacji o typie, w zależności od tego, czy liczba zależności projektu i innymi czynnikami wydajnościowymi systemu. **Zakończ** przycisk jest niedostępny podczas ładowania, chyba że **ponownie użyj typów w przywoływanych zestawach** pole wyboru jest zaznaczone.

5. Kliknij przycisk **Zakończ** po zakończeniu.

Podczas wyświetlania postępu, narzędzie:

* Pobiera metadane z usługi WCF.
* Generuje kod odwołania usługi w pliku o nazwie *reference.cs*i dodaje go do projektu w obszarze **podłączone usługi** węzła.
* Aktualizuje plik projektu (.csproj) za pomocą odwołania do pakietu NuGet wymagane do kompilowania i uruchamiania na platformie docelowej.

![Visual Studio postępu okna](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Po ukończeniu tych procesów, można utworzyć wystąpienia typu wygenerowanego klienta WCF i wywoływanie operacji usługi.

## <a name="next-steps"></a>Następne kroki

### <a name="feedback--questions"></a>Opinie i pytania

Jeśli masz pytania lub opinie, [Otwórz problem w serwisie GitHub](https://github.com/dotnet/wcf/issues/new). Możesz również sprawdzić wszelkie istniejące pytania lub problemy [w repozytorium usługi WCF w usłudze GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Uwagi do wersji

* Zapoznaj się [informacje o wersji](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) uzyskać informacje o zaktualizowanej wersji, w tym znanych problemów.
