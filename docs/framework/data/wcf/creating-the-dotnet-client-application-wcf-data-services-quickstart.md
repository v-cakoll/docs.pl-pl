---
title: Tworzenie aplikacji klienckiej .NET Framework (Usługi danych programu WCF Szybki Start)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 9995a509bf997298d991a1f66cfdf3cae6cd0395
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790966"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>Tworzenie aplikacji klienckiej .NET Framework (Usługi danych programu WCF Szybki Start)

To jest końcowe zadanie Usługi danych programu WCF szybkiego startu. W tym zadaniu zostanie dodana Aplikacja konsolowa do rozwiązania, Dodaj odwołanie do [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanału informacyjnego do tej nowej aplikacji klienckiej i dostęp do źródła strumieniowego OData z aplikacji klienckiej przy użyciu wygenerowanych klas usługi danych klienta i bibliotek klienckich .

> [!NOTE]
> Aplikacja kliencka oparta na .NET Framework nie jest wymagana w celu uzyskania dostępu do strumieniowego źródła danych. Dostęp do usługi danych mogą uzyskać każdy składnik aplikacji korzystający z kanału informacyjnego OData. Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi danych w aplikacji klienckiej](using-a-data-service-in-a-client-application-wcf-data-services.md).

## <a name="to-create-the-client-application-by-using-visual-studio"></a>Aby utworzyć aplikację kliencką przy użyciu programu Visual Studio

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.

2. W lewym okienku wybierz pozycję **zainstalowane** > [ **C# Visual** lub **Visual Basic**] > **Windows Desktop**, a następnie wybierz szablon **Aplikacja WPF** .

3. Wprowadź `NorthwindClient` nazwę projektu, a następnie kliknij przycisk **OK**.

4. Otwórz plik MainWindow. XAML i Zastąp kod XAML następującym kodem:

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a>Aby dodać odwołanie do usługi danych do projektu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt NorthwindClient, kliknij polecenie **Dodaj** > **odwołanie do usługi**, a następnie kliknij przycisk **odkryj**.

     Spowoduje to wyświetlenie usługi danych Northwind utworzonej w pierwszym zadaniu.

2. W polu tekstowym **przestrzeń nazw** wpisz `Northwind`, a następnie kliknij przycisk **OK**.

     Spowoduje to dodanie nowego pliku kodu do projektu, który zawiera klasy danych, które są używane do uzyskiwania dostępu do zasobów usługi danych i korzystania z nich jako obiekty. Klasy danych są tworzone w przestrzeni nazw `NorthwindClient.Northwind`.

## <a name="to-access-data-service-data-in-the-wpf-application"></a>Aby uzyskać dostęp do danych usługi danych w aplikacji WPF

1. W **Eksplorator rozwiązań** w obszarze **NorthwindClient**kliknij prawym przyciskiem myszy projekt, a następnie kliknij pozycję **Dodaj odwołanie**.

2. W oknie dialogowym **Dodaj odwołanie** kliknij kartę **.NET** , wybierz zestaw system. Data. Services. Client. dll, a następnie kliknij przycisk **OK**.

3. W **Eksplorator rozwiązań** w obszarze **NorthwindClient**Otwórz stronę kodową dla pliku MainWindow. XAML i Dodaj następującą `using` instrukcję (`Imports` w Visual Basic).

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. Wstaw następujący kod, który wysyła zapytanie do tej usługi danych i wiąże wynik z <xref:System.Data.Services.Client.DataServiceCollection%601> `MainWindow` klasą:

    > [!NOTE]
    > Należy zastąpić nazwę `localhost:12345` hosta serwerem i portem, który hostuje wystąpienie usługi danych Northwind.

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. Wstaw następujący kod, który zapisuje zmiany w `MainWindow` klasie:

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a>Aby skompilować i uruchomić aplikację NorthwindClient

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt NorthwindClient i wybierz pozycję **Ustaw jako projekt startowy**.

2. Naciśnij klawisz **F5** , aby uruchomić aplikację.

     Spowoduje to skompilowanie rozwiązania i uruchomienie aplikacji klienckiej. Dane są żądane z usługi i wyświetlane w konsoli programu.

3. Edytuj wartość w kolumnie **ilość** siatki danych, a następnie kliknij przycisk **Zapisz**.

     Zmiany są zapisywane w usłudze danych.

    > [!NOTE]
    > Ta wersja aplikacji NorthwindClient nie obsługuje dodawania i usuwania jednostek.

## <a name="next-steps"></a>Następne kroki

Pomyślnie utworzono aplikację kliencką, która uzyskuje dostęp do przykładowego źródła danych Northwind OData. Ukończono również Usługi danych programu WCF przewodnika Szybki Start.

Aby uzyskać więcej informacji na temat uzyskiwania dostępu do źródła danych OData z aplikacji .NET Framework, zobacz [usługi danych programu WCF Library Client](wcf-data-services-client-library.md).

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](getting-started-with-wcf-data-services.md)
- [Zasoby](wcf-data-services-resources.md)
