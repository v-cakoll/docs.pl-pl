---
title: Tworzenie aplikacji klienckich programu .NET Framework (WCF Data Services — Szybki Start)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: efea92fa5176641ac64265dfffd44a088115bb61
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305939"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>Tworzenie aplikacji klienckich programu .NET Framework (WCF Data Services — Szybki Start)

To jest ostatnim zadaniem tego przewodnika Szybki Start usług danych WCF. W ramach tego zadania będzie dodać aplikację konsolową w języku z rozwiązaniem, Dodaj odwołanie do [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych do tej nowej aplikacji klienta i dostępu do źródła danych z aplikacji klienckiej przy użyciu klas usługi danych wygenerowanego klienta i bibliotek klienta OData .

> [!NOTE]
> Aplikacja kliencka oparte na programie .NET Framework nie jest wymagany dostęp do danych z kanału informacyjnego. Usługa danych jest możliwy przez dowolny składnik aplikacji, który zużywa źródła danych OData. Aby uzyskać więcej informacji, zobacz [przy użyciu usługi danych w aplikacji klienckiej](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).

## <a name="to-create-the-client-application-by-using-visual-studio"></a>Aby utworzyć aplikację klienta w programie Visual Studio

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.

2. W okienku po lewej stronie wybierz **zainstalowane** > [**Visual C#**  lub **języka Visual Basic**] > **pulpitu Windows**, a następnie wybierz pozycję  **Aplikacja WPF** szablonu.

3. Wprowadź `NorthwindClient` nazwę projektu, a następnie kliknij przycisk **OK**.

4. Otwórz plik MainWindow.xaml i Zastąp kod XAML następującym kodem:

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a>Aby dodać odwołanie do usługi danych, do projektu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt NorthwindClient, kliknij przycisk **Dodaj** > **odwołanie do usługi**, a następnie kliknij przycisk **odnajdowania** .

     Spowoduje to wyświetlenie Usługa danych Northwind, który został utworzony w pierwszym zadaniu.

2. W **Namespace** polu tekstowym `Northwind`, a następnie kliknij przycisk **OK**.

     To dodaje nowy plik kodu do projektu, który zawiera klasy danych, które są używane do uzyskania dostępu i korzystać z zasobów usługi danych jako obiekty. Klasy danych są tworzone w przestrzeni nazw `NorthwindClient.Northwind`.

## <a name="to-access-data-service-data-in-the-wpf-application"></a>Dostęp do danych usługi danych w aplikacji WPF

1. W **Eksploratora rozwiązań** w obszarze **NorthwindClient**, kliknij prawym przyciskiem myszy projekt i kliknij przycisk **Dodaj odwołanie**.

2. W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** karty, wybierz zestaw System.Data.Services.Client.dll, a następnie kliknij **OK**.

3. W **Eksploratora rozwiązań** w obszarze **NorthwindClient**, otwórz stronę kodową dla pliku MainWindow.xaml i Dodaj następujący kod `using` — instrukcja (`Imports` w języku Visual Basic).

     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]

3. Wstaw następujący kod, który wykonuje kwerendę usługi danych i wiąże wynik, który ma <xref:System.Data.Services.Client.DataServiceCollection%601> do `MainWindow` klasy:

    > [!NOTE]
    > Należy zastąpić nazwę hosta `localhost:12345` za pomocą serwera i port, który jest hostem Twoje wystąpienie usługi danych Northwind.

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]

4. Wstaw następujący kod, który zapisuje zmiany w `MainWindow` klasy:

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a>Aby skompilować i uruchomić aplikację NorthwindClient

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt NorthwindClient i wybierz **Ustaw jako projekt startowy**.

2. Naciśnij klawisz **F5** do uruchomienia aplikacji.

     Kompiluje rozwiązanie i uruchamia aplikację klienta. Dane są wymagane usługi i wyświetlane w konsoli.

3. Edytowanie wartości w **ilość** kolumny siatki danych, a następnie kliknij przycisk **Zapisz**.

     Zmiany są zapisywane do usługi danych.

    > [!NOTE]
    > Ta wersja aplikacji NorthwindClient nie obsługuje dodawanie i usuwanie jednostek.

## <a name="next-steps"></a>Następne kroki

Pomyślnie utworzono aplikację kliencką, która uzyskuje dostęp do przykładowej, którą Northwind strumieniowego źródła OData. Również ukończono Przewodnik Szybki Start usług danych WCF!

Aby więcej informacji na temat uzyskiwania dostępu do OData Kanał informacyjny z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji, zobacz [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [Zasoby](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
