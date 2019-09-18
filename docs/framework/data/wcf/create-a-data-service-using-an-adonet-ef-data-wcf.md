---
title: 'Instrukcje: Tworzenie usługi danych przy użyciu źródła danych ADO.NET Entity Framework (Usługi danych programu WCF)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 8c597738d656b32e7b4c75246027b726f425c6ef
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053015"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Instrukcje: Tworzenie usługi danych przy użyciu źródła danych ADO.NET Entity Framework (Usługi danych programu WCF)

Usługi danych programu WCF udostępnia dane jednostki jako usługę danych. Te dane jednostki są udostępniane przez platformę ADO. webentity Framework, gdy źródłem danych jest relacyjna baza danych. W tym temacie pokazano, jak utworzyć model danych oparty na Entity Framework w aplikacji sieci Web programu Visual Studio, która jest oparta na istniejącej bazie danych, i korzystać z tego modelu danych w celu utworzenia nowej usługi danych.

Entity Framework udostępnia również narzędzie wiersza polecenia, które może generować model Entity Framework poza projektem programu Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Użyj programu EdmGen. exe, aby wygenerować model i pliki](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)mapowania.

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Aby dodać model Entity Framework, który jest oparty na istniejącej bazie danych w istniejącej aplikacji sieci Web

1. W menu **projekt** kliknij polecenie **Dodaj** > **nowy element**.

2. W okienku **Szablony** kliknij kategorię **dane** , a następnie wybierz pozycję **ADO.NET Entity Data Model**.

3. Wprowadź nazwę modelu, a następnie kliknij przycisk **Dodaj**.

     Zostanie wyświetlona pierwsza strona kreatora Entity Data Model.

4. W oknie dialogowym **Wybierz zawartość modelu** wybierz pozycję **Generuj z bazy danych**. Następnie kliknij przycisk **Dalej**.

5. Kliknij przycisk **nowe połączenie** .

6. W oknie dialogowym **Właściwości połączenia** wpisz nazwę serwera, wybierz metodę uwierzytelniania, wpisz nazwę bazy danych, a następnie kliknij przycisk **OK**.

     Okno dialogowe **Wybieranie połączenia danych** zostanie zaktualizowane przy użyciu ustawień połączenia z bazą danych.

7. Upewnij się, że pole wyboru **Zapisz ustawienia połączenia jednostek w pliku App. config as:** jest zaznaczone. Następnie kliknij przycisk **Dalej**.

8. W oknie dialogowym **Wybierz obiekty bazy danych** wybierz wszystkie obiekty bazy danych, które planujesz uwidocznić w usłudze danych.

    > [!NOTE]
    > Obiekty zawarte w modelu danych nie są automatycznie uwidaczniane przez usługę danych. Muszą być jawnie udostępniane przez samą usługę. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).

9. Kliknij przycisk **Zakończ** , aby zakończyć pracę kreatora.

     Spowoduje to utworzenie domyślnego modelu danych opartego na określonej bazie danych. Entity Framework umożliwia dostosowanie modelu danych. Aby uzyskać więcej informacji, zobacz [Entity Data Model narzędzia zadań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Aby utworzyć usługę danych przy użyciu nowego modelu danych

1. W programie Visual Studio Otwórz plik. edmx, który reprezentuje model danych.

2. W **przeglądarce modelu**kliknij prawym przyciskiem myszy Model, kliknij polecenie **Właściwości**, a następnie zanotuj nazwę kontenera jednostek.

3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij pozycję **Dodaj** > **nowy element**.

4. W oknie dialogowym **Dodaj nowy element** wybierz szablon **usługi danych programu WCF** w kategorii **Sieć Web** .

   ![Szablon elementu usługi danych programu WCF w programie Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Szablon **usługi danych programu WCF** jest dostępny w programie visual Studio 2015, ale nie w programie visual Studio 2017.

5. Podaj nazwę usługi, a następnie kliknij przycisk **OK**.

     Program Visual Studio tworzy znaczniki XML i pliki kodu dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu.

6. W kodzie usługi danych Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który dziedziczy <xref:System.Data.Objects.ObjectContext> z klasy i jest kontenerem jednostek modelu danych, który został zanotowany w kroku 2.

7. W kodzie usługi danych Włącz autoryzowanych klientów, aby uzyskać dostęp do zestawów jednostek udostępnianych przez usługę danych. Aby uzyskać więcej informacji, zobacz [Tworzenie usługi danych](creating-the-data-service.md).

8. Aby przetestować usługę danych Northwind. svc przy użyciu przeglądarki sieci Web, postępuj zgodnie z instrukcjami podanymi w temacie [Uzyskiwanie dostępu do usługi z przeglądarki sieci Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
- [Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia](create-a-data-service-using-rp-wcf-data-services.md)
- [Instrukcje: Tworzenie usługi danych przy użyciu LINQ to SQL źródła danych](create-a-data-service-using-linq-to-sql-wcf.md)
