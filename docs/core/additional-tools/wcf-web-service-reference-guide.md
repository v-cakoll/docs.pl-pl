---
title: Dodaj odwołanie do usługi sieci Web WCF
description: Przegląd narzędzia Microsoft WCF Web Service Reference Provider, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobnie jak Dodaj odwołanie do usługi dla projektów .NET Framework.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: feecf374e1af48f349495c13ea91b810c6b0a1c3
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191897"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>Korzystanie z narzędzia dostawcy odwołań usługi sieci Web programu WCF

W ciągu lat wiele deweloperów programu Visual Studio korzystało z wydajności, którą zapewnia narzędzie [**Dodaj odwołanie do usługi**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) , gdy .NET Framework projekty potrzebują dostępu do usług sieci Web.  Narzędzie **referencyjne usługi sieci Web WCF** to rozszerzenie usługi połączonej z programem Visual Studio, które zapewnia środowisko, takie jak Dodaj odwołanie do usługi funkcje dla projektów .NET Core i ASP.NET Core. To narzędzie pobiera metadane z usługi sieci Web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub z pliku WSDL i generuje plik źródłowy zgodny z programem .NET Core zawierający kod serwera proxy klienta Windows Communication Foundation (WCF), którego można użyć w celu uzyskania dostępu do sieci Web. usługi.

> [!IMPORTANT]
> Należy tylko odwoływać się do usług z zaufanego źródła. Dodanie odwołań z niezaufanego źródła może spowodować naruszenie zabezpieczeń.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017 w wersji 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) lub nowszej

## <a name="how-to-use-the-extension"></a>Jak używać rozszerzenia

> [!NOTE]
> Opcja **odwołania do usługi sieci Web programu WCF** ma zastosowanie do projektów utworzonych przy użyciu następujących szablonów projektu:
>
> - **Visual C#**   >  **.NET Core**
> - **Visual C#**   >  **.NET Standard**
> - **Aplikacja internetowa**  **C# programu Visual**  > **Web**  >  ASP.NET Core

Korzystając z szablonu projektu **ASP.NET Core aplikacji sieci Web** , w tym artykule opisano sposób dodawania do projektu odwołania do usługi WCF:

1. W Eksplorator rozwiązań kliknij dwukrotnie węzeł **usługi połączone** w projekcie (dla projektu .NET Core lub .NET Standard, ta opcja jest dostępna po kliknięciu prawym przyciskiem myszy węzła **zależności** projektu w Eksplorator rozwiązań).

    Zostanie wyświetlona strona **połączone usługi** , jak pokazano na poniższej ilustracji:

    ![Karta usługi połączone programu Visual Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Na stronie **podłączone usługi** kliknij pozycję **Microsoft WCF Web Service Reference Provider**. Spowoduje to wyświetlenie kreatora **konfiguracji odwołania usługi sieci Web programu WCF** :

    ![Karta punktu końcowego usługi Visual Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Wybierz usługę.

    art. W kreatorze **konfiguracji odwołania usługi sieci Web programu WCF** dostępne są kilka opcji wyszukiwania usług:

     * Aby wyszukać usługi zdefiniowane w bieżącym rozwiązaniu, kliknij przycisk **odkryj** .
     * Aby wyszukać usługi hostowane w określonym adresie, wprowadź adres URL usługi w polu **adres** , a następnie kliknij przycisk **Przejdź** .
     * Aby wybrać plik WSDL zawierający informacje o metadanych usługi sieci Web, kliknij przycisk **Przeglądaj** .

    3b. Wybierz usługę z listy wyników wyszukiwania w polu **usługi** . W razie potrzeby wprowadź przestrzeń nazw dla wygenerowanego kodu w polu tekstowym odpowiadające mu **przestrzeń nazw** .

    3C. Kliknij przycisk **dalej** , aby otworzyć **Opcje typu danych** i strony **Opcje klienta** . Alternatywnie kliknij przycisk **Zakończ** , aby użyć opcji domyślnych.

4. Formularz **Opcje typu danych** umożliwia uściślenie ustawień konfiguracji wygenerowanych odwołań do usługi:

    ![Karta Opcje typu danych programu Visual Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > Opcja **Użyj ponownie typów w przywoływanych zestawach** jest przydatna, gdy typy danych potrzebne do generowania kodu odwołania do usługi są zdefiniowane w jednym z zestawów, do których się odwołuje.  Ważne jest, aby ponownie użyć istniejących typów danych, aby uniknąć konfliktów typu czas kompilacji lub problemów w czasie wykonywania.

    Podczas ładowania informacji o typie może wystąpić opóźnienie, w zależności od liczby zależności projektu i innych czynników wydajności systemu. Przycisk **Zakończ** jest wyłączony podczas ładowania, chyba że pole wyboru **ponowne używanie typów w przywoływanych zestawach** nie jest zaznaczone.

5. Po zakończeniu kliknij przycisk **Zakończ** .

Podczas wyświetlania postępu narzędzie:

- Pobiera metadane z usługi WCF.
- Generuje kod odwołania do usługi w pliku o nazwie *Reference.cs*i dodaje go do projektu w węźle **usługi połączone** .
- Aktualizuje plik projektu (. csproj) odwołania do pakietów NuGet wymagane do kompilowania i uruchamiania na platformie docelowej.

![Okno postępu programu Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Po zakończeniu tych procesów można utworzyć wystąpienie wygenerowanego typu klienta WCF i wywołać operacje usługi.

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji Windows Communication Foundation](../../framework/wcf/getting-started-tutorial.md)
- [Usługi Windows Communication Foundation i usługi danych programu WCF w programie Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [Funkcje obsługiwane przez program WCF na platformie .NET Core](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a>Opinie & pytania

Jeśli masz jakieś pytania lub opinie, zgłoś je w [społeczności deweloperów](https://developercommunity.visualstudio.com/) za pomocą narzędzia [Zgłoś problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) .

## <a name="release-notes"></a>Uwagi do wersji

- Zapoznaj się z informacjami o [wersji](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) dotyczącymi zaktualizowanych informacji o wersji, w tym znanych problemów.
