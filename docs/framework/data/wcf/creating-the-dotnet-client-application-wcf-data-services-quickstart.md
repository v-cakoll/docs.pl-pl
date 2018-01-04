---
title: "Tworzenie aplikacji klienckich programu .NET Framework (Szybki Start usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 563d08a5907c8248a74ba992de17ac3dd0679827
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>Tworzenie aplikacji klienckich programu .NET Framework (Szybki Start usługi danych WCF)
To zadanie końcowego [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Szybki Start. W tym zadaniu zostanie dodać aplikację konsoli do rozwiązania, Dodaj odwołanie do [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych w tym nową aplikację klienta, a dostęp [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych z aplikacji klienta przy użyciu klasy usługi danych wygenerowanego klienta i klienta biblioteki.  
  
> [!NOTE]
>  Aplikacja kliencka opartych na programie .NET Framework nie jest wymagane dostępu do danych, źródła danych. Usługi danych są dostępne dla każdego składnika aplikacji, który wykorzystuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Aby uzyskać więcej informacji, zobacz [przy użyciu usługi danych w aplikacji klienckiej](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
### <a name="to-create-the-client-application-by-using-visual-studio"></a>Aby utworzyć aplikację klienta przy użyciu programu Visual Studio  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **typy projektów**, kliknij przycisk **Windows**, a następnie wybierz **aplikacji WPF** w **szablony** okienka.  
  
3.  Wprowadź `NorthwindClient` nazwę projektu, a następnie kliknij przycisk **OK**.  
  
4.  Otwórz plik MainWindow.xaml i Zastąp kod XAML z następującym kodem:  
  
     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### <a name="to-add-a-data-service-reference-to-the-project"></a>Aby dodać odwołania do danych usługi do projektu  
  
1.  Kliknij prawym przyciskiem myszy projekt NorthwindClient, kliknij przycisk **Dodaj odwołanie do usługi**, a następnie kliknij przycisk **odnajdowania**.  
  
     Spowoduje to wyświetlenie utworzoną w pierwszym zadaniu usługę danych Northwind.  
  
2.  W **Namespace** polu tekstowym `Northwind`, a następnie kliknij przycisk **OK**.  
  
     Spowoduje to dodanie nowego pliku kodu projektu, który zawiera klasy danych, które są używane do uzyskania dostępu i interakcji z zasobami usługi danych jako obiekty. Klasy danych są tworzone w obszarze nazw `NorthwindClient.Northwind`.  
  
### <a name="to-access-data-service-data-in-the-wpf-application"></a>Dostęp do danych usługi danych w aplikacji WPF  
  
1.  W **Eksploratora rozwiązań** w obszarze **NorthwindClient**, kliknij prawym przyciskiem myszy projekt i kliknij przycisk **Dodaj odwołanie**.  
  
2.  W oknie dialogowym Dodawanie odwołania, kliknij przycisk **.NET** , wybierz zestaw System.Data.Services.Client.dll, a następnie kliknij **OK**. W **Eksploratora rozwiązań** w obszarze **NorthwindClient**, otwórz stronę kodu dla pliku MainWindow.xaml i Dodaj następujący `using` instrukcji (`Imports` w języku Visual Basic).  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  Wstaw następujący kod, który wysyła zapytanie do tej usługi danych i wiąże wynik, który ma <xref:System.Data.Services.Client.DataServiceCollection%601> do `MainWindow` klasy:  
  
    > [!NOTE]
    >  Należy zastąpić nazwą hosta `localhost:12345` z serwera i port, który jest hostem Twoje wystąpienie usługi danych Northwind.  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  Wstaw następujący kod, który zapisuje zmiany w `MainWindow` klasy:  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### <a name="to-build-and-run-the-northwindclient-application"></a>Aby skompilować i uruchomić aplikację NorthwindClient  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt NorthwindClient i wybierz **Ustaw jako projekt startowy**.  
  
2.  Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Buduje rozwiązanie i uruchamia aplikację klienta. Dane są wymagane przez usługę i wyświetlane w konsoli.  
  
3.  Edytowanie wartości w **ilość** kolumny Siatka danych, a następnie kliknij przycisk **zapisać**.  
  
     Zmiany są zapisywane do usługi danych.  
  
    > [!NOTE]
    >  Ta wersja aplikacji NorthwindClient nie obsługuje dodawania i usuwania jednostek.  
  
## <a name="next-steps"></a>Następne kroki  
 Pomyślnie utworzono aplikacji klienckiej, która uzyskuje dostęp do przykładowej Northwind [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Ukończono również [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Szybki Start. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Uzyskiwanie dostępu do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji, zobacz [biblioteki klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Zasoby](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
