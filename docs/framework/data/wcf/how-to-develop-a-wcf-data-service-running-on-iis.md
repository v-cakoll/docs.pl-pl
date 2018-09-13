---
title: 'Porady: Tworzenie usługi danych WCF działającej na serwerze IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: af81e65dfd4661d62d7aa4a3e6075be312765cb7
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710200"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Porady: Tworzenie usługi danych WCF działającej na serwerze IIS

W tym temacie pokazano, jak używać usługi danych WCF w celu utworzenia usługi danych, która jest oparta na bazie danych Northwind, która jest hostowana przez aplikację sieci Web programu ASP.NET, która jest uruchomiona na Internet Information Services (IIS). Aby uzyskać przykład sposobu tworzenia tych samych Usługa danych Northwind jako aplikację sieci Web programu ASP.NET, która działa na serwerze ASP.NET Development Server, zobacz [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

> [!NOTE]
> Aby utworzyć usługę danych Northwind, należy zainstalowano przykładowej bazy danych Northwind na komputerze lokalnym. Aby pobrać tej przykładowej bazy danych, zobacz stronę pobierania [przykładowych baz danych programu SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).

 W tym temacie przedstawiono sposób tworzenia usługi danych przy użyciu dostawcy środowiska Entity Framework. Innych dostawców usług danych są dostępne. Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).

 Po utworzeniu usługi, musisz jawnie określić dostęp do zasobów usługi danych. Aby uzyskać więcej informacji, zobacz [porady: Włączanie dostępu do usługi danych](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>Utwórz aplikację sieci web ASP.NET, która działa na serwerze IIS

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. W **nowy projekt** okno dialogowe, wybierz opcję **zainstalowane** > [**Visual C#** lub **języka Visual Basic**] > **wsieciWeb** kategorii.

3. Wybierz **aplikacji sieci Web ASP.NET** szablonu.

1. Wprowadź `NorthwindService` jako nazwę projektu.

5. Kliknij przycisk **OK**.

6. Na **projektu** menu, wybierz opcję **właściwości NorthwindService**.

7. Wybierz **Web** , a następnie wybierz pozycję **użycia lokalnego serwera sieci Web usług IIS**.

8. Kliknij przycisk **Utwórz katalog wirtualny** a następnie kliknij przycisk **OK**.

9. W wierszu polecenia z uprawnieniami administratora wykonaj jedną z następujących poleceń (w zależności od systemu operacyjnego):

    -   systemy 32-bitowe:

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    -   systemy 64-bitowe:

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Dzięki temu czy Windows Communication Foundation (WCF) jest zarejestrowana na komputerze.

10. W wierszu polecenia z uprawnieniami administratora wykonaj jedną z następujących poleceń (w zależności od systemu operacyjnego):

    -   systemy 32-bitowe:

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    -   systemy 64-bitowe:

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     To sprawia, że się upewnić, że usługi IIS działa poprawnie po zainstalowaniu programu WCF na komputerze. Może być również ponowne uruchomienie usług IIS.

11. Po uruchomieniu aplikacji ASP.NET w usługach IIS7, należy wykonać następujące czynności:

    1. Otwórz Menedżera usług IIS i przejdź do aplikacji PhotoService w ramach **domyślna witryna sieci Web**.

    2. W **widoku funkcji**, kliknij dwukrotnie **uwierzytelniania**.

    3. Na **uwierzytelniania** wybierz opcję **uwierzytelnianie anonimowe**.

    4. W **akcje** okienku kliknij **Edytuj** można ustawić zabezpieczeń, jednostki, w którym użytkownicy anonimowi będą łączyć się z witryny.

    5. W **edytowanie poświadczeń uwierzytelniania anonimowego** okno dialogowe, wybierz opcję **tożsamość puli aplikacji**.

    > [!IMPORTANT]
    > Gdy używasz konta Usługa sieciowa, udzielasz anonimowym użytkownikom wszystkich dostępu do sieci wewnętrznej powiązanej z tego konta.

12. Za pomocą programu SQL Server Management Studio, narzędzia sqlcmd.exe lub edytora języka Transact-SQL w programie Visual Studio, wykonaj następujące polecenie języka Transact-SQL dla wystąpienia programu SQL Server, który zawiera bazę danych Northwind, dołączone:

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    Spowoduje to utworzenie nazwy logowania w wystąpieniu programu SQL Server dla konta Windows używane do uruchamiania usług IIS. Dzięki temu usługi IIS, aby nawiązać połączenie z wystąpieniem programu SQL Server.

13. Z bazy danych Northwind, dołączony wykonaj następujące polecenia języka Transact-SQL:

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

    Spowoduje to przydzielenie uprawnień do nowego identyfikatora użytkownika, który umożliwia usługom IIS do odczytu i zapisu danych w bazie danych Northwind.

## <a name="define-the-data-model"></a>Zdefiniowanie modelu danych

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij **Dodaj** > **nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **ADO.NET Entity Data Model**.

3. Nazwa modelu danych, wpisz `Northwind.edmx`.

4. W kreatorze modelu danych jednostki, wybierz **Generuj z bazy danych**, a następnie kliknij przycisk **dalej**.

5. Połączenia z bazą danych modelu danych, wykonując jedną z następujących czynności, a następnie kliknij przycisk **dalej**:

    -   Jeśli nie masz połączenia z bazą danych już skonfigurowane, kliknij przycisk **nowe połączenie** i Utwórz nowe połączenie. Aby uzyskać więcej informacji, zobacz [porady: tworzenie połączeń bazy danych SQL Server](https://go.microsoft.com/fwlink/?LinkId=123631). To wystąpienie programu SQL Server musi mieć bazie danych Northwind dołączone.

         \- lub —

    -   Jeśli masz już skonfigurowane do łączenia z bazą danych Northwind połączenia z bazą danych, wybierz połączenie z listy połączeń.

6. Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie usuń zaznaczenie pól wyboru dla widoków i procedur składowanych.

7. Kliknij przycisk **Zakończ** aby zamknąć kreatora.

## <a name="create-the-data-service"></a>Utworzenie usługi danych

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij **Dodaj** > **nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF**.

   ![Szablon elementu usługi danych WCF w programie Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **Usługi danych WCF** szablon jest dostępny w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

3. Wprowadź nazwę usługi `Northwind`.

     Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu. W **Eksploratora rozwiązań**, usługa ma nazwę, Northwind i rozszerzenia. svc.cs lub. svc.vb.

4. W kodzie dla usługi danych, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostki w modelu danych, który w tym przypadku jest `NorthwindEntities`. Definicja klasy powinna wyglądać to następujące czynności:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Zobacz także

- [Udostępnianie danych jako usługi](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
