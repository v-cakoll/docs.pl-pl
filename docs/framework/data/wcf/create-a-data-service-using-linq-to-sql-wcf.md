---
title: 'Porady: Tworzenie usługi danych przy użyciu LINQ do SQL źródła danych (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: e65d9dc48f128d7808f0731057ec0a5e52e65444
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798482"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Porady: Tworzenie usługi danych przy użyciu LINQ do SQL źródła danych (WCF Data Services)

Usługi danych WCF przedstawia dane jednostki w postaci usługi danych. Dostawca odbicia pozwala na zdefiniowanie modelu danych, który opiera się na każdej klasy, która udostępnia elementy Członkowskie zwracające <xref:System.Linq.IQueryable%601> implementacji. Aby można było zaktualizować dane w źródle danych, w ramach tych zajęć musi implementować też <xref:System.Data.Services.IUpdatable> interfejsu. Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md). W tym temacie dowiesz się, jak utworzyć LINQ do klas SQL, uzyskujących dostęp do przykładowej bazy danych Northwind za pomocą dostawcy odbicia, a także jak utworzyć usługę danych, która opiera się na tych klas danych.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>Aby dodać LINQ do klas SQL do projektu

1. Z aplikacji Visual Basic lub C# na **projektu** menu, kliknij przycisk **Dodaj** > **nowy element**.

2. Kliknij przycisk **klasy LINQ do SQL** szablonu.

3. Zmień nazwę na **Northwind.dbml**.

4. Kliknij przycisk **Dodaj**.

     Plik Northwind.dbml zostanie dodany do projektu, i otwiera Object Relational Designer (O/R Designer).

5. W **serwera**/**Eksplorator bazy danych**, w obszarze Northwind, rozwiń węzeł **tabel** i przeciągnij `Customers` tabeli do Object Relational Designer (O/R Projektant).

     A `Customer` Klasa jednostki jest utworzony i wyświetlony na powierzchni projektowej.

6. Powtórz krok 6 dla `Orders`, `Order_Details`, i `Products` tabel.

7. Kliknij prawym przyciskiem myszy nowy plik dbml, który reprezentuje LINQ do klas SQL i kliknij przycisk **Wyświetl kod**.

     Spowoduje to utworzenie nowej strony związanym z kodem o nazwie Northwind.cs, który zawiera definicję klasy częściowej klasy dziedziczącej z klasy <xref:System.Data.Linq.DataContext> klasy, która jest w tym przypadku `NorthwindDataContext`.

8. Zastąp zawartość pliku z kodem Northwind.cs następującym kodem. Ten kod implementuje dostawcy odbicia, rozszerzając <xref:System.Data.Linq.DataContext> i klas danych generowanych przez LINQ to SQL:

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Aby utworzyć usługę danych za pomocą LINQ do modelu danych programu SQL

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij **Dodaj** > **nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF** szablonu z **Web** kategorii.

   ![Szablon elementu usługi danych WCF w programie Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **Usługi danych WCF** szablon jest dostępny w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

3. Podaj nazwę usługi, a następnie kliknij przycisk **OK**.

     Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu.

4. W kodzie dla usługi danych, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostki w modelu danych, który w tym przypadku jest `NorthwindDataContext`.

5. W kodzie dla usługi danych, Zastąp kod symbolu zastępczego `InitializeService` funkcji następującym kodem:

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]

     Dzięki temu autoryzowanych klientów dostępu do zasobów dla trzech zestawów określonej jednostki.

6. Aby przetestować usługę danych Northwind.svc przy użyciu przeglądarki sieci Web, postępuj zgodnie z instrukcjami w temacie [uzyskiwania dostępu do usługi z przeglądarki sieci Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)