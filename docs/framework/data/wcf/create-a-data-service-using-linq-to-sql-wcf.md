---
title: "Porady: Tworzenie usługi danych za pomocą LINQ do SQL źródła danych (usługi danych WCF)"
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
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 755df7c86d80214ded4e8c9534f88910a171c7a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Porady: Tworzenie usługi danych za pomocą LINQ do SQL źródła danych (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]udostępnia dane jednostki jako usługa danych. Dostawca odbicia umożliwia zdefiniowanie modelu danych, która jest oparta na dowolnej klasy, która udostępnia elementy Członkowskie zwracające <xref:System.Linq.IQueryable%601> implementacji. Aby można było dokonać aktualizacji danych w źródle danych, również musi implementować następujące klasy <xref:System.Data.Services.IUpdatable> interfejsu. Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md). W tym temacie przedstawiono sposób tworzenia LINQ w klasach SQL, które uzyskują dostęp do przykładowej bazy danych Northwind przy użyciu dostawcy odbicia, a także sposób utworzyć usługę danych, która jest oparta na tych klas danych.  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a>Aby dodać LINQ w klasach SQL do projektu  
  
1.  Z poziomu aplikacji Visual Basic lub C# na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  Kliknij przycisk **klasy LINQ do SQL** szablonu.  
  
3.  Zmień nazwę, aby **Northwind.dbml**.  
  
4.  Kliknij przycisk **Dodaj**.  
  
     Plik Northwind.dbml zostanie dodany do projektu i otwiera Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych).  
  
5.  W **serwera**/**Eksploratora bazy danych**, w obszarze Northwind, rozwiń węzeł **tabel** i przeciągnij `Customers` tabeli w Projektancie obiektów relacyjnych (obiektów relacyjnych Projektant).  
  
     A `Customer` klasy jednostka jest tworzony i wyświetlany na powierzchni projektu.  
  
6.  Powtórz kroki od 6 do `Orders`, `Order_Details`, i `Products` tabel.  
  
7.  Kliknij prawym przyciskiem myszy nowy plik .dbml, który reprezentuje LINQ do SQL klas i kliknij przycisk **kod widoku**.  
  
     Spowoduje to utworzenie nowej strony związane z kodem o nazwie Northwind.cs, który zawiera definicję klasy częściowej klasy, która dziedziczy po <xref:System.Data.Linq.DataContext> klasy, która jest w tym przypadku `NorthwindDataContext`.  
  
8.  Zastąp zawartość pliku kodu Northwind.cs następującym kodem. Ten kod implementuje dostawcę odbicia rozszerzając <xref:System.Data.Linq.DataContext> i klas danych wygenerowanych przez składnik LINQ to SQL:  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Aby utworzyć usługę danych za pomocą LINQ do SQL na podstawie danych modelu  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij przycisk **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF**.  
  
3.  Podaj nazwę usługi, a następnie kliknij przycisk **OK**.  
  
     Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu.  
  
4.  W kodzie dla usługi data, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych o typie kontenera jednostek w modelu danych, który w tym przypadku jest `NorthwindDataContext`.  
  
5.  W kodzie dla usługi data, Zastąp kod symbol zastępczy w `InitializeService` funkcji z następujących czynności:  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     Dzięki temu autoryzowanym klientom dostęp do zasobów dla trzech zestawów określonej jednostki.  
  
6.  Aby przetestować usługę Northwind.svc danych za pomocą przeglądarki sieci Web, postępuj zgodnie z instrukcjami w temacie [uzyskiwania dostępu do usługi z przeglądarką sieci Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
