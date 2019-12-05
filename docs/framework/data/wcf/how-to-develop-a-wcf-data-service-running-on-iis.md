---
title: 'Instrukcje: Tworzenie usługi danych programu WCF uruchomionej w usługach IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 684361dbb97e70296a3061f71102662023f88d9a
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800511"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Instrukcje: Tworzenie usługi danych programu WCF uruchomionej w usługach IIS

W tym temacie pokazano, jak za pomocą Usługi danych programu WCF utworzyć usługę danych opartą na przykładowej bazie danych Northwind, która jest hostowana przez aplikację sieci Web ASP.NET działającą w usłudze Internet Information Services (IIS). Aby zapoznać się z przykładem tworzenia tej samej usługi danych Northwind jako aplikacji sieci Web ASP.NET działającej na serwerze deweloperskim ASP.NET, zobacz [Przewodnik Szybki start usługi danych programu WCF](quickstart-wcf-data-services.md).

> [!NOTE]
> Aby utworzyć usługę danych Northwind, na komputerze lokalnym musi być zainstalowana Przykładowa baza danych Northwind. Aby pobrać tę przykładową bazę danych, zobacz stronę pobierania, [przykładowe bazy danych dla SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).

W tym temacie przedstawiono sposób tworzenia usługi danych przy użyciu dostawcy Entity Framework. Inni dostawcy usług danych są dostępni. Aby uzyskać więcej informacji, zobacz [Data Services Providers](data-services-providers-wcf-data-services.md).

Po utworzeniu usługi należy jawnie zapewnić dostęp do zasobów usługi danych. Aby uzyskać więcej informacji, zobacz [jak: Włączanie dostępu do usługi danych](how-to-enable-access-to-the-data-service-wcf-data-services.md).

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>Tworzenie aplikacji sieci Web ASP.NET działającej w usługach IIS

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy** **projekt** > .

2. W oknie dialogowym **Nowy projekt** wybierz **zainstalowaną** > [**Visual C#**  lub **Visual Basic**] > kategorii **sieci Web** .

3. Wybierz szablon **aplikacji sieci Web ASP.NET** .

4. Wprowadź `NorthwindService` jako nazwę projektu.

5. Kliknij przycisk **OK**.

6. W menu **projekt** wybierz pozycję **Właściwości NorthwindService**.

7. Wybierz kartę **Sieć Web** , a następnie wybierz pozycję **Użyj lokalnego serwera sieci Web usług IIS**.

8. Kliknij pozycję **Utwórz katalog wirtualny** , a następnie kliknij przycisk **OK**.

9. W wierszu polecenia z uprawnieniami administratora wykonaj jedno z następujących poleceń (w zależności od systemu operacyjnego):

    - 32-bitowe systemy:

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - Systemy 64-bitowe:

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Upewnij się, że na komputerze zarejestrowano Windows Communication Foundation (WCF).

10. W wierszu polecenia z uprawnieniami administratora wykonaj jedno z następujących poleceń (w zależności od systemu operacyjnego):

    - 32-bitowe systemy:

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - Systemy 64-bitowe:

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     Gwarantuje to, że usługi IIS działają prawidłowo po zainstalowaniu programu WCF na komputerze. Może być również konieczne ponowne uruchomienie usług IIS.

11. Gdy aplikacja ASP.NET jest uruchomiona na IIS7, należy również wykonać następujące czynności:

    1. Otwórz Menedżera usług IIS i przejdź do aplikacji do obsługi w obszarze **Domyślna witryna sieci Web**.

    2. W obszarze **Widok funkcji**kliknij dwukrotnie pozycję **uwierzytelnianie**.

    3. Na stronie **uwierzytelnianie** wybierz opcję **uwierzytelnianie anonimowe**.

    4. W okienku **Akcje** kliknij pozycję **Edytuj** , aby ustawić podmiot zabezpieczeń, pod którym anonimowi użytkownicy będą łączyć się z lokacją.

    5. W oknie dialogowym **Edytowanie poświadczeń uwierzytelniania anonimowego** wybierz pozycję **tożsamość puli aplikacji**.

    > [!IMPORTANT]
    > Korzystając z konta usługi sieciowej, należy przyznać anonimowym użytkownikom dostęp do sieci wewnętrznej skojarzonej z tym kontem.

12. Za pomocą SQL Server Management Studio, narzędzia sqlcmd. exe lub edytora Transact-SQL w programie Visual Studio wykonaj następujące polecenie języka Transact-SQL względem wystąpienia SQL Server z załączoną bazą danych Northwind:

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    Spowoduje to utworzenie nazwy logowania w wystąpieniu SQL Server dla konta systemu Windows używanego do uruchamiania usług IIS. Dzięki temu usługi IIS mogą łączyć się z wystąpieniem SQL Server.

13. Po dołączeniu bazy danych Northwind wykonaj następujące polecenia języka Transact-SQL:

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

    Powoduje to przyznanie praw do nowej nazwy logowania, co umożliwia usługom IIS odczytywanie danych i zapisywanie ich w bazie danych Northwind.

## <a name="define-the-data-model"></a>Zdefiniowanie modelu danych

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij pozycję **Dodaj** > **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **ADO.NET Entity Data Model**.

3. W polu Nazwa modelu danych wpisz `Northwind.edmx`.

4. W Kreatorze Entity Data Model wybierz pozycję **Generuj z bazy danych**, a następnie kliknij przycisk **dalej**.

5. Aby połączyć model danych z bazą danych, wykonaj jedną z następujących czynności, a następnie kliknij przycisk **dalej**:

    - Jeśli nie masz już skonfigurowanego połączenia z bazą danych, kliknij pozycję **nowe połączenie** i Utwórz nowe połączenie. Aby uzyskać więcej informacji, zobacz [How to: Create Connections to SQL Server Databases](https://go.microsoft.com/fwlink/?LinkId=123631). To wystąpienie SQL Server musi mieć dołączoną przykładową bazę danych Northwind.

         \- lub —

    - Jeśli masz już połączenie z bazą danych do łączenia się z bazą danych Northwind, wybierz to połączenie z listy połączeń.

6. Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie wyczyść pola wyboru dla widoków i procedur składowanych.

7. Kliknij przycisk **Zakończ** , aby zamknąć kreatora.

## <a name="create-the-data-service"></a>Utworzenie usługi danych

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij pozycję **Dodaj** > **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Usługa danych WCF**.

   ![Szablon elementu usługi danych programu WCF w programie Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Szablon **usługi danych programu WCF** jest dostępny w programie visual Studio 2015, ale nie w programie visual Studio 2017 lub nowszym.

3. W polu Nazwa usługi wprowadź `Northwind`.

     Program Visual Studio tworzy znaczniki XML i pliki kodu dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu. W **Eksplorator rozwiązań**usługa ma nazwę, Northwind i rozszerzenie. svc.cs lub. svc. vb.

4. W kodzie usługi danych Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostek modelu danych, które w tym przypadku jest `NorthwindEntities`. Definicja klasy powinna wyglądać następująco:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Zobacz także

- [Udostępnianie danych jako usługi](exposing-your-data-as-a-service-wcf-data-services.md)
