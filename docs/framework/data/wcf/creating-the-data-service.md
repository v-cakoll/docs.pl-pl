---
title: "Tworzenie usługi danych"
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
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d890e4c2041ae4c70a79adfc0ab4141402fcd3f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="creating-the-data-service"></a>Tworzenie usługi danych
W ramach tego zadania spowoduje utworzenie usługa dane przykładowe z wykorzystaniem [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] do udostępnienia [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych, która jest oparta na bazie danych Northwind. Zadanie obejmuje następujące podstawowe czynności:  
  
1.  Utwórz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji sieci Web.  
  
2.  Zdefiniuj modelu danych przy użyciu [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] narzędzia.  
  
3.  Dodaj usługę danych do aplikacji sieci Web.  
  
4.  Zapewnianie dostępu do usługi danych.  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Aplikacji sieci Web, który jest tworzony podczas wykonania tego zadania jest uruchamiany [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server udostępnione przez [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Programowanie serwer obsługuje tylko dostęp z komputera lokalnego. Można również ułatwić testowanie i rozwiązywanie problemów z usługą danych podczas tworzenia, Rozważ uruchomienie aplikacji, która obsługuje usługę danych przy użyciu usług Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych WCF działającą na serwerze IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
### <a name="to-create-the-aspnet-web-application"></a>Aby utworzyć aplikację sieci Web ASP.NET  
  
1.  W [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]na **pliku** menu, wybierz opcję **nowy**, a następnie wybierz **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, w obszarze albo [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] wybierz **Web** szablonu, a następnie wybierz **aplikacji sieci Web ASP.NET**.  
  
    > [!NOTE]
    >  Jeśli używasz [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] deweloperów sieci Web, należy utworzyć nową witrynę sieci Web zamiast nowej aplikacji sieci Web.  
  
3.  Typ `NorthwindService` jako nazwę projektu.  
  
4.  Kliknij przycisk **OK**.  
  
5.  (Opcjonalnie) Określ numer portu określonych dla aplikacji sieci Web. Uwaga: numer portu `12345` jest używany w pozostałej części szybkiego startu.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu został właśnie utworzony, a następnie kliknij przycisk **właściwości**.  
  
    2.  Wybierz **Web** , a następnie ustaw wartość **określonego portu** pole tekstowe służące do `12345`.  
  
### <a name="to-define-the-data-model"></a>Aby zdefiniować modelu danych  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, a następnie kliknij przycisk **Dodaj nowy element.**  
  
2.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **danych** szablonu, a następnie wybierz **modelu danych jednostki ADO.NET**.  
  
3.  Wpisz nazwę modelu danych, `Northwind.edmx`.  
  
4.  W [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] kreatora wybierz opcję **generowania z bazy danych**, a następnie kliknij przycisk **dalej**.  
  
5.  Połączenia z bazą danych modelu danych, wykonując jedną z następujących czynności, a następnie kliknij przycisk **dalej**:  
  
    -   Jeśli nie masz już skonfigurowane połączenie z bazą danych, kliknij przycisk **nowe połączenie** i Utwórz nowe połączenie. Aby uzyskać więcej informacji, zobacz [porady: tworzenie połączeń bazy danych programu SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631). To [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] wystąpienie musi mieć bazie danych Northwind dołączony.  
  
         \-lub -  
  
    -   Jeśli masz już skonfigurowana do łączenia z bazą danych Northwind połączenia z bazą danych, wybierz połączenie z listy połączeń.  
  
6.  Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie usuń zaznaczenie pól wyboru dla widoków i procedur składowanych.  
  
7.  Kliknij przycisk **Zakończ** aby zamknąć kreatora.  
  
    > [!NOTE]
    >  Ten model danych wygenerowanych przedstawia właściwości klucza obcego w typach jednostek. Utworzone przy użyciu modeli danych [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 nie ma tych właściwości klucza obcego. W związku z tym należy zaktualizować wszystkie aplikacje klienckie, które zostały utworzone w celu uzyskania dostępu do usługi danych Northwind, który został utworzony przy użyciu klasy usługi danych klienta [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 przed podjęciem próby dostęp do tej wersji usługi danych Northwind.  
  
### <a name="to-create-the-data-service"></a>Aby utworzyć usługę danych  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę Twojej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, a następnie kliknij przycisk **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF**.  
  
3.  Wpisz nazwę usługi, `Northwind`.  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu. W **Eksploratora rozwiązań**, usługa będzie mieć nazwę, Northwind, z rozszerzeniem. svc.cs lub. svc.vb.  
  
4.  W kodzie dla usługi data, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych o typie kontenera jednostek w modelu danych, który w tym przypadku jest `NorthwindEntities`. Definicja klasy powinien wyglądać to następujące czynności:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a>Aby umożliwić dostęp do zasobów usługi danych  
  
1.  W kodzie dla usługi data, Zastąp kod symbol zastępczy w `InitializeService` funkcji z następujących czynności:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Dzięki temu autoryzowanych klientów miał do odczytu i zapisu do zasobów dla zestawów określonej jednostki.  
  
    > [!NOTE]
    >  Każdy klient, który można uzyskać dostępu do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji również dostęp do zasobów udostępnianych przez usługę danych. W usłudze danych w środowisku produkcyjnym aby uniemożliwić nieautoryzowany dostęp do zasobów należy również zabezpieczyć samej aplikacji. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie usługi danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Pomyślnie utworzono nową usługę danych, który ujawnia [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, która jest oparta na bazie danych Northwind, a ma włączony dostęp do źródła dla klientów, które mają uprawnienia do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji sieci Web. Następnie powoduje uruchomienie usługi danych z [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] i będą uzyskiwać dostęp do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła strumieniowego poprzez przesłanie żądania HTTP GET za pośrednictwem przeglądarki sieci Web:  
  
 [Uzyskiwanie dostępu do usługi z przeglądarki internetowej](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
