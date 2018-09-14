---
title: 'Porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 72439596ec6dc6c42024ed38116ba0026922154c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514602"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework (WCF Data Services)

Usługi danych WCF przedstawia dane jednostki w postaci usługi danych. Dane te jednostki są udostępniane przez [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] po relacyjnej bazy danych w źródle danych. W tym temacie przedstawiono sposób tworzenia [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]— na podstawie modelu danych w aplikacji internetowego programu Visual Studio, która opiera się na istniejącą bazę danych i Utwórz nową usługę danych przy użyciu tego modelu danych.

[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Także narzędzia wiersza polecenia, które mogą generować [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] modelu spoza projektu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: użycie EdmGen.exe do generowania modelu i mapowania plików](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Aby dodać modelu Entity Framework, która opiera się na istniejącą bazę danych do istniejącej aplikacji sieci Web

1. Na **projektu** menu, kliknij przycisk **Dodaj** > **nowy element**.

2. W **szablony** okienku kliknij **danych** kategorii, a następnie wybierz **ADO.NET Entity Data Model**.

3. Wprowadź nazwę modelu, a następnie kliknij przycisk **Dodaj**.

     Na pierwszej stronie [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] zostanie wyświetlony Kreator.

4. W **wybierz zawartość modelu** okno dialogowe, wybierz opcję **Generuj z bazy danych**. Następnie kliknij przycisk **Dalej**.

5. Kliknij przycisk **nowe połączenie** przycisku.

6. W **właściwości połączenia** okno dialogowe, wpisz nazwę serwera, wybierz metodę uwierzytelniania, wpisz nazwę bazy danych, a następnie kliknij przycisk **OK**.

     **Wybierz połączenie danych**s, okno dialogowe zostanie zaktualizowana przy użyciu ustawienia połączenia bazy danych.

7. Upewnij się, że **zapisywanie ustawień połączenia w pliku App.Config jako jednostki:** zaznaczono pole wyboru. Następnie kliknij przycisk **Dalej**.

8. W **wybierz obiekty bazy danych** okno dialogowe, zaznacz wszystkie bazy danych obiekty czy planowane jest udostępnianie w usłudze danych.

    > [!NOTE]
    > Obiektów uwzględnionych w modelu danych nie są automatycznie widoczne przez usługę danych. One muszą być wyraźnie widoczne za samą usługę. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

9. Kliknij przycisk **Zakończ** aby zakończyć działanie kreatora.

     Spowoduje to utworzenie domyślny model danych, na podstawie określonej bazy danych. [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Umożliwia dostosowywanie modelu danych. Aby uzyskać więcej informacji, zobacz [zadania](https://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Aby utworzyć usługę danych przy użyciu nowego modelu danych

1. W programie Visual Studio Otwórz plik edmx, reprezentujące model danych.

2. W **przeglądarka modeli**, kliknij prawym przyciskiem myszy model, kliknij przycisk **właściwości**, a następnie zanotuj nazwę kontenera jednostek.

3. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę swojej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, a następnie kliknij przycisk **Dodaj** > **nowy element**.

4. W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF** szablonu w **Web** kategorii.

   ![Szablon elementu usługi danych WCF w programie Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **Usługi danych WCF** szablon jest dostępny w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

5. Podaj nazwę usługi, a następnie kliknij przycisk **OK**.

     Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu.

6. W kodzie dla usługi danych, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych o typie, który dziedziczy z <xref:System.Data.Objects.ObjectContext> klasy i oznacza to kontener jednostek w modelu danych, która została zanotowanym w kroku 2.

7. W kodzie dla usługi danych należy włączyć autoryzowanym klientom dostęp zestawy jednostek usługi ujawnia w danych. Aby uzyskać więcej informacji, zobacz [Tworzenie usługi danych](../../../../docs/framework/data/wcf/creating-the-data-service.md).

8. Aby przetestować usługę danych Northwind.svc przy użyciu przeglądarki sieci Web, postępuj zgodnie z instrukcjami w temacie [uzyskiwania dostępu do usługi z przeglądarki sieci Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Zobacz też

- [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych LINQ to SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)