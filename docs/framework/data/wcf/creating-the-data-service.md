---
title: Tworzenie usługi danych programu WCF w programie Visual Studio
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: c3c80fb48635199f45acb1e72bf756bbc65d2e14
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780408"
---
# <a name="create-the-data-service"></a>Utworzenie usługi danych

W tym temacie opisano Tworzenie przykładowej usługi danych korzystającej z usługi danych programu WCF w celu udostępnienia [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanału informacyjnego opartego na przykładowej bazie danych Northwind. Zadanie obejmuje następujące podstawowe kroki:

1. Utwórz aplikację sieci Web ASP.NET.

2. Zdefiniuj model danych przy użyciu narzędzi Entity Data Model.

3. Dodaj usługę danych do aplikacji sieci Web.

4. Włącz dostęp do usługi danych.

## <a name="create-the-aspnet-web-app"></a>Tworzenie aplikacji sieci Web ASP.NET

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** w obszarze Visual Basic lub C# wizualizacji wybierz kategorię **sieci Web** , a następnie wybierz pozycję **aplikacja sieci Web ASP.NET**.

1. Wprowadź `NorthwindService` jako nazwę projektu, a następnie wybierz przycisk **OK**.

1. W oknie dialogowym **Nowa aplikacja sieci Web ASP.NET** wybierz opcję **pusty** , a następnie wybierz przycisk **OK**.

1. Obowiązkowe Określ konkretny numer portu dla aplikacji sieci Web. Uwaga: numer `12345` portu jest używany w tej serii tematów szybkiego startu.

    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt ASP.NET, który właśnie został utworzony, a następnie wybierz polecenie **Właściwości**.

    2. Wybierz kartę **Sieć Web** , a następnie ustaw wartość pola tekstowego **określony port** na `12345`.

## <a name="define-the-data-model"></a>Zdefiniowanie modelu danych

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij pozycję **Dodaj** > **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz kategorię **dane** , a następnie wybierz pozycję **ADO.NET Entity Data Model**.

3. W polu Nazwa modelu danych wprowadź `Northwind.edmx`.

4. W **kreatorze Entity Data Model**wybierz pozycję **Dr Designer z bazy danych**, a następnie kliknij przycisk **dalej**.

5. Aby połączyć model danych z bazą danych, wykonaj jedną z następujących czynności, a następnie kliknij przycisk **dalej**:

    - Jeśli nie masz już skonfigurowanego połączenia z bazą danych, kliknij pozycję **nowe połączenie** i Utwórz nowe połączenie. Aby uzyskać więcej informacji, zobacz [jak: Utwórz połączenia z bazami](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))danych SQL Server. To wystąpienie SQL Server musi mieć dołączoną przykładową bazę danych Northwind.

         \- lub —

    - Jeśli masz już połączenie z bazą danych do łączenia się z bazą danych Northwind, wybierz to połączenie z listy połączeń.

6. Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie wyczyść pola wyboru dla widoków i procedur składowanych.

7. Kliknij przycisk **Zakończ** , aby zamknąć kreatora.

## <a name="create-the-wcf-data-service"></a>Tworzenie usługi danych programu WCF

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt ASP.NET, a następnie wybierz polecenie **Dodaj** > **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz szablon elementu **usługi danych programu WCF** z kategorii **sieci Web** .

   ![Szablon elementu usługi danych programu WCF w programie Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Szablon **usługi danych programu WCF** jest dostępny w programie visual Studio 2015, ale nie w programie visual Studio 2017.

3. W polu Nazwa usługi wpisz `Northwind`.

     Program Visual Studio tworzy znaczniki XML i pliki kodu dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu. W **Eksplorator rozwiązań**usługa ma nazwę Northwind z rozszerzeniem *. svc.cs* lub *. svc. vb*.

4. W kodzie usługi danych Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostek modelu danych, w tym `NorthwindEntities`przypadku. Definicja klasy powinna wyglądać następująco:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a>Zapewnianie dostępu do zasobów usługi danych

1. W kodzie usługi danych Zastąp symbol zastępczy w `InitializeService` funkcji następującymi elementami:

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     Dzięki temu autoryzowani klienci mają dostęp do odczytu i zapisu do zasobów dla określonych zestawów jednostek.

    > [!NOTE]
    > Każdy klient, który może uzyskać dostęp do aplikacji ASP.NET, może również uzyskać dostęp do zasobów udostępnianych przez usługę danych. W usłudze danych produkcyjnych aby zapobiec nieautoryzowanemu dostępowi do zasobów, należy również zabezpieczyć samą aplikację. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usługi danych programu WCF](securing-wcf-data-services.md).

## <a name="next-steps"></a>Następne kroki

Pomyślnie utworzono nową usługę danych, która udostępnia strumieniowe dane OData oparte na przykładowej bazie danych Northwind, i włączono dostęp do kanału informacyjnego dla klientów, którzy mają uprawnienia do aplikacji sieci Web ASP.NET. Następnie należy uruchomić usługę danych z programu Visual Studio i uzyskać dostęp do źródła strumieniowego OData przez przesłanie żądań HTTP GET za pośrednictwem przeglądarki sieci Web:

> [!div class="nextstepaction"]
> [Uzyskiwanie dostępu do usługi z przeglądarki sieci Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Zobacz także

- [Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
