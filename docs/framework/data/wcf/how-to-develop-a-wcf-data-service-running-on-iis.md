---
title: 'Instrukcje: Tworzenie usługi danych WCF działającej na serwerze IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 8a1a0c2c55267940463e2c9ab82bb52345269260
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121614"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Jak: Tworzenie usługi danych WCF działającej na usługach IIS

W tym artykule pokazano, jak używać usług WCF Data Services do tworzenia usługi danych opartej na przykładowej bazie danych Northwind, która jest obsługiwana przez ASP.NET aplikację sieci Web działającą w internetowych usługach informacyjnych (IIS). Na przykład sposobu tworzenia tej samej usługi danych Northwind jako ASP.NET aplikacji sieci Web, która działa na serwerze ASP.NET Development Server, zobacz [szybki start usług danych WCF](quickstart-wcf-data-services.md).

> [!NOTE]
> Aby utworzyć usługę danych Northwind, najpierw zainstaluj przykładową bazę danych Northwind na komputerze lokalnym. Aby zainstalować bazę danych, uruchom skrypt Transact-SQL z [northwind i pubów przykładowych baz danych dla programu Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).

W tym artykule pokazano, jak utworzyć usługę danych przy użyciu dostawcy struktury encji. Dostępne są inni dostawcy usług danych. Aby uzyskać więcej informacji, zobacz [Dostawcy usług danych](data-services-providers-wcf-data-services.md).

Po utworzeniu usługi należy jawnie zapewnić dostęp do zasobów usługi danych. Aby uzyskać więcej informacji, zobacz [Jak: Włączanie dostępu do usługi danych](how-to-enable-access-to-the-data-service-wcf-data-services.md).

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>Tworzenie ASP.NET aplikacji sieci web, która działa w serwisach IIS

1. W programie Visual Studio w menu **Plik** wybierz polecenie **Nowy** > **projekt**.

2. W oknie dialogowym **Nowy projekt** wybierz kategorię **Zainstalowana** > [**Visual C#** lub **Visual Basic**] > **sieci Web.**

3. Wybierz **szablon ASP.NET aplikacji sieci Web.**

4. Wprowadź `NorthwindService` jako nazwę projektu.

5. Kliknij przycisk **OK**.

6. W menu **Projekt** wybierz polecenie **Właściwości usługi NorthwindService**.

7. Wybierz kartę **Sieć Web,** a następnie wybierz pozycję **Użyj lokalnego serwera sieci Web usług IIS**.

8. Kliknij **pozycję Utwórz katalog wirtualny,** a następnie kliknij przycisk **OK**.

9. W wierszu polecenia z uprawnieniami administratora wykonaj jedno z następujących poleceń (w zależności od systemu operacyjnego):

    - Systemy 32-bitowe: 

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - Systemy 64-bitowe: 

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Dzięki temu program Windows Communication Foundation (WCF) jest zarejestrowany na komputerze.

10. W wierszu polecenia z uprawnieniami administratora wykonaj jedno z następujących poleceń (w zależności od systemu operacyjnego):

    - Systemy 32-bitowe: 

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - Systemy 64-bitowe: 

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     Dzięki temu usługi IIS są poprawnie uruchamiane po zainstalowaniu w cf na komputerze. Może być konieczne również ponowne uruchomienie iis.

11. Gdy aplikacja ASP.NET działa w serwisie IIS7, należy również wykonać następujące kroki:

    1. Otwórz Menedżera usług IIS i przejdź do aplikacji PhotoService w obszarze **Domyślna witryna sieci Web**.

    2. W **widoku funkcji**kliknij dwukrotnie pozycję **Uwierzytelnianie**.

    3. Na stronie **Uwierzytelnianie** wybierz pozycję **Uwierzytelnianie anonimowe**.

    4. W okienku **Akcje** kliknij przycisk **Edytuj,** aby ustawić podmiot zabezpieczeń, w którym anonimowi użytkownicy będą łączyć się z witryną.

    5. W oknie dialogowym **Edytowanie poświadczeń uwierzytelniania anonimowego** wybierz pozycję **Tożsamość puli aplikacji**.

    > [!IMPORTANT]
    > Korzystając z konta Usługa sieciowa, udzielasz użytkownikom anonimowym całego dostępu do sieci wewnętrznej skojarzonego z tym kontem.

12. Za pomocą programu SQL Server Management Studio, sqlcmd.exe lub Edytora Transact-SQL w programie Visual Studio należy wykonać następujące polecenie Transact-SQL względem wystąpienia programu SQL Server z dołączoną bazą danych Northwind:

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    Spowoduje to utworzenie logowania w wystąpieniu programu SQL Server dla konta systemu Windows używanego do uruchamiania usług IIS. Dzięki temu usługi IIS mogą łączyć się z wystąpieniem programu SQL Server.

13. Po dołączeniu bazy danych Northwind wykonaj następujące polecenia Transact-SQL:

    ```sql
    USE Northwind
    GO
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];
    GO
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]
    WITH DEFAULT_DATABASE=[Northwind];
    GO
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    ```

    Daje to prawa do nowego logowania, co umożliwia iIS odczytywanie danych z bazy danych Northwind i zapisywanie ich.

## <a name="define-the-data-model"></a>Zdefiniowanie modelu danych

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij polecenie **Dodaj** > **nowy element**.

2. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję ADO.NET model danych **jednostki**.

3. Aby uzyskać nazwę modelu danych, wpisz . `Northwind.edmx`

4. W Kreatorze modelu danych encji wybierz pozycję **Generuj z bazy danych,** a następnie kliknij przycisk **Dalej**.

5. Połącz model danych z bazą danych, wykonując jedną z następujących czynności, a następnie kliknij przycisk **Dalej:**

    - Jeśli połączenie z bazą danych nie jest już skonfigurowane, kliknij pozycję **Nowe połączenie** i utwórz nowe połączenie. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie połączeń z bazami danych programu SQL Server](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). To wystąpienie programu SQL Server musi mieć dołączoną przykładową bazę danych Northwind.

         \-lub -

    - Jeśli masz połączenie z bazą danych już skonfigurowane do łączenia się z bazą danych Northwind, wybierz to połączenie z listy połączeń.

6. Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych i wyczyść pola wyboru dla widoków i procedur przechowywanych.

7. Kliknij **przycisk Zakończ,** aby zamknąć kreatora.

## <a name="create-the-data-service"></a>Utworzenie usługi danych

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij polecenie **Dodaj** > **nowy element**.

2. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Usługa danych **WCF**.

   ![Szablon elementu usługi danych WCF w programie Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Szablon **usługi danych WCF** jest dostępny w programie Visual Studio 2015, ale nie w programie Visual Studio 2017 lub nowszym.

3. Aby uzyskać nazwę usługi, `Northwind`wprowadź .

     Program Visual Studio tworzy znaczniki XML i pliki kodu dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu. W **Eksploratorze rozwiązań**usługa ma nazwę Northwind i rozszerzenie .svc.cs lub .svc.vb.

4. W kodzie dla usługi danych `/* TODO: put your data source class name here */` zastąp komentarz w definicji klasy, która definiuje usługę danych, typem, który `NorthwindEntities`jest kontenerem jednostki modelu danych, który w tym przypadku jest . Definicja klasy powinna wyglądać następująco:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Zobacz też

- [Udostępnianie danych jako usługi](exposing-your-data-as-a-service-wcf-data-services.md)
