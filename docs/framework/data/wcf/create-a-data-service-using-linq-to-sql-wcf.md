---
title: 'Instrukcje: Tworzenie usługi danych przy użyciu LINQ to SQL źródła danych (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: cde5b9903a1fd164ce106a6a408ac4bb79976642
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802283"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Instrukcje: Tworzenie usługi danych przy użyciu LINQ to SQL źródła danych (Usługi danych programu WCF)

Usługi danych programu WCF udostępnia dane jednostki jako usługę danych. Dostawca odbicia umożliwia zdefiniowanie modelu danych, który jest oparty na dowolnej klasie, która uwidacznia elementy członkowskie, które zwracają implementację <xref:System.Linq.IQueryable%601>. Aby móc wprowadzać aktualizacje danych w źródle danych, te klasy muszą również implementować interfejs <xref:System.Data.Services.IUpdatable>. Aby uzyskać więcej informacji, zobacz [Data Services Providers](data-services-providers-wcf-data-services.md). W tym temacie przedstawiono sposób tworzenia klas LINQ to SQL, które uzyskują dostęp do przykładowej bazy danych Northwind przy użyciu dostawcy odbicia, a także sposobu tworzenia usługi danych opartej na tych klasach danych.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>Aby dodać klasy LINQ to SQL do projektu

1. Z poziomu C# Visual Basic lub aplikacji w menu **projekt** kliknij polecenie **Dodaj** > **nowy element**.

2. Kliknij szablon **LINQ to SQL klas** .

3. Zmień nazwę na **Northwind. dbml**.

4. Kliknij przycisk **Dodaj**.

     Plik Northwind. dbml jest dodawany do projektu, a Object Relational Designer (Projektant O/R) zostanie otwarty.

5. W **Eksplorator bazy danych** **serwer**/w obszarze Northwind rozwiń węzeł **tabele** i przeciągnij tabelę `Customers` na Object Relational Designer (Projektant O/R).

     Klasa jednostki `Customer` jest tworzona i pojawia się na powierzchni projektowej.

6. Powtórz krok 6 dla tabel `Orders`, `Order_Details`i `Products`.

7. Kliknij prawym przyciskiem myszy nowy plik. dbml, który reprezentuje klasy LINQ to SQL i kliknij polecenie **Wyświetl kod**.

     Spowoduje to utworzenie nowej strony powiązanej z kodem o nazwie Northwind.cs, która zawiera definicję klasy częściowej dla klasy, która dziedziczy z klasy <xref:System.Data.Linq.DataContext>, która w tym przypadku jest `NorthwindDataContext`.

8. Zastąp zawartość pliku kodu Northwind.cs następującym kodem. Ten kod implementuje dostawcę odbicia, rozszerzając <xref:System.Data.Linq.DataContext> i klasy danych wygenerowane przez LINQ to SQL:

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Aby utworzyć usługę danych przy użyciu modelu danych opartego na LINQ to SQL

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij pozycję **Dodaj** > **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz szablon **usługi danych programu WCF** z kategorii **Sieć Web** .

   ![Szablon elementu usługi danych programu WCF w programie Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Szablon **usługi danych programu WCF** jest dostępny w programie visual Studio 2015, ale nie w programie visual Studio 2017 lub nowszym.

3. Podaj nazwę usługi, a następnie kliknij przycisk **OK**.

     Program Visual Studio tworzy znaczniki XML i pliki kodu dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu.

4. W kodzie usługi danych Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostek modelu danych, które w tym przypadku jest `NorthwindDataContext`.

5. W kodzie usługi danych Zastąp symbol zastępczy w funkcji `InitializeService` następującym:

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     Dzięki temu autoryzowani klienci mogą uzyskać dostęp do zasobów dla trzech określonych zestawów jednostek.

6. Aby przetestować usługę danych Northwind. svc przy użyciu przeglądarki sieci Web, postępuj zgodnie z instrukcjami podanymi w temacie [Uzyskiwanie dostępu do usługi z przeglądarki sieci Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia](create-a-data-service-using-rp-wcf-data-services.md)
- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
