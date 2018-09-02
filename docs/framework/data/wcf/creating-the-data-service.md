---
title: Tworzenie usługi danych WCF w programie Visual Studio
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: d7ab227a19eeb9bf054700f8d932b75cf3c1ddc9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417830"
---
# <a name="create-the-data-service"></a>Utworzenie usługi danych

W tym temacie utworzysz usługi danych przykładowych, która używa usługi danych WCF w celu udostępnienia [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych, który jest oparty na bazie danych Northwind. Zadanie obejmuje następujące podstawowe kroki:

1. Tworzenie aplikacji sieci Web platformy ASP.NET.

2. Zdefiniowanie modelu danych za pomocą narzędzi Entity Data Model.

3. Dodaj usługę danych do aplikacji sieci Web.

4. Zapewnianie dostępu do usługi danych.

## <a name="create-the-aspnet-web-app"></a>Tworzenie aplikacji sieci web platformy ASP.NET

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

1. W **nowy projekt** okna dialogowego wybierz pozycję Visual Basic lub Visual C# **Web** kategorii, a następnie wybierz **aplikacji sieci Web ASP.NET**.

1. Wprowadź `NorthwindService` jako nazwę projektu, a następnie wybierz pozycję **OK**.

1. W **Nowa aplikacja internetowa ASP.NET** okno dialogowe, wybierz opcję **pusty** , a następnie wybierz **OK**.

1. (Opcjonalnie) Określ określonego numeru portu dla aplikacji sieci Web. Uwaga: numer portu `12345` jest używany w tej serii tematy w przewodniku Szybki Start.

    1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy na projekt ASP.NET, który został utworzony, a następnie wybierz **właściwości**.

    2. Wybierz **Web** , a następnie ustaw wartość **określonego portu** pole tekstowe do `12345`.

## <a name="define-the-data-model"></a>Zdefiniowanie modelu danych

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij **Dodaj** > **nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **danych** kategorii, a następnie wybierz **ADO.NET Entity Data Model**.

3. Nazwa modelu danych, można wprowadzić `Northwind.edmx`.

4. W **Kreator modelu Entity Data Model**, wybierz opcję **projektancie platformy EF z bazy danych**, a następnie kliknij przycisk **dalej**.

5. Połączenia z bazą danych modelu danych, wykonując jedną z następujących czynności, a następnie kliknij przycisk **dalej**:

    -   Jeśli nie masz połączenia z bazą danych już skonfigurowane, kliknij przycisk **nowe połączenie** i Utwórz nowe połączenie. Aby uzyskać więcej informacji, zobacz [porady: tworzenie połączeń bazy danych SQL Server](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). To wystąpienie programu SQL Server musi mieć bazie danych Northwind dołączone.

         \- lub —

    -   Jeśli masz już skonfigurowane do łączenia z bazą danych Northwind połączenia z bazą danych, wybierz połączenie z listy połączeń.

6. Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie usuń zaznaczenie pól wyboru dla widoków i procedur składowanych.

7. Kliknij przycisk **Zakończ** aby zamknąć kreatora.

## <a name="create-the-wcf-data-service"></a>Tworzenie usługi danych WCF

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem platformy ASP.NET, a następnie wybierz **Dodaj** > **nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF** szablonu elementu z **Web** kategorii.

   ![Szablon elementu usługi danych WCF w programie Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **Usługi danych WCF** szablon jest dostępny w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

3. Aby uzyskać nazwę usługi, wpisz `Northwind`.

     Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu. W **Eksploratora rozwiązań**, usługa ma nazwę Northwind z rozszerzeniem *. svc.cs* lub *. svc.vb*.

4. W kodzie dla usługi danych, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który jest kontenerem jednostki w modelu danych, który w tym przypadku jest `NorthwindEntities`. Definicja klasy powinna wyglądać to następujące czynności:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a>Zapewnianie dostępu do zasobów usługi danych

1. W kodzie dla usługi danych, Zastąp kod symbolu zastępczego `InitializeService` funkcji następującym kodem:

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]

     Dzięki temu autoryzowanych klientów do odczytu i zapisu do zasobów dla określonej jednostki zestawów.

    > [!NOTE]
    > Każdy klient, który może uzyskiwać dostęp do aplikacji ASP.NET również dostęp do zasobów udostępnianych przez usługę danych. W środowisku produkcyjnym usługi danych Aby uniemożliwić nieautoryzowany dostęp do zasobów należy również zabezpieczyć samej aplikacji. Aby uzyskać więcej informacji, zobacz [zabezpieczania usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).

## <a name="next-steps"></a>Następne kroki

Pomyślnie utworzono nową usługę danych, która uwidoczni źródło OData opartego na bazie danych Northwind i włączono dostęp do źródła danych dla klientów, które mają uprawnienia do aplikacji sieci Web ASP.NET. Następnie będzie uruchomić usługi danych z programu Visual Studio i dostęp do źródła danych przez przesłanie żądania HTTP GET, za pośrednictwem przeglądarki sieci Web OData:

> [!div class="nextstepaction"]
> [Dostęp do usługi z przeglądarki sieci web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Zobacz także

- [Narzędzia do modelu danych jednostki ADO.NET](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)