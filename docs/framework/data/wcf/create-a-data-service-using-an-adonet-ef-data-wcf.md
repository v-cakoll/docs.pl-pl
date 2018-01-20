---
title: "Porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e90b11800685707460171e5e2d250ef757979c44
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]udostępnia dane jednostki jako usługa danych. Dane te jednostki są udostępniane przez [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] po relacyjnej bazy danych w źródle danych. W tym temacie przedstawiono sposób tworzenia [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]— na podstawie modelu danych w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] sieci Web aplikacji, która jest oparta na istniejącej bazy danych i umożliwia utworzenie nowej usługi danych tego modelu danych.  
  
 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Udostępnia narzędzie wiersza polecenia, które mogą generować [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] modelu poza [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] projektu. Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do generowania modelu i mapowania plików](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Aby dodać model narzędzia Entity Framework, która jest oparta na istniejącej bazy danych do istniejącej aplikacji sieci Web  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  W **szablony** okienku, kliknij przycisk **danych** kategorii, a następnie wybierz **modelu danych jednostki ADO.NET**.  
  
3.  Wpisz nazwę modelu, a następnie kliknij przycisk **Dodaj**.  
  
     Na pierwszej stronie [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] zostanie wyświetlony Kreator.  
  
4.  W **wybierz zawartość modelu** okno dialogowe, wybierz opcję **generowania z bazy danych**. Następnie kliknij przycisk **Dalej**.  
  
5.  Kliknij przycisk **nowe połączenie** przycisku.  
  
6.  W **właściwości połączenia** okno dialogowe, wpisz nazwę serwera, wybierz metodę uwierzytelniania, wpisz nazwę bazy danych i kliknięcie **OK**.  
  
     **Wybierz połączenie danych**okno dialogowe s został zaktualizowany o ustawienia połączenia bazy danych.  
  
7.  Upewnij się, że **jednostki Zapisz ustawienia połączenia w pliku App.Config jako:** jest zaznaczone pole wyboru. Następnie kliknij przycisk **Dalej**.  
  
8.  W **wybierz obiekty bazy danych użytkownika** okno dialogowe, wybierz wszystkie bazy danych obiektów planuje udostępnić w usłudze danych.  
  
    > [!NOTE]
    >  Liczba obiektów uwzględnionych w modelu danych nie są automatycznie widoczne przez usługę danych. One musi być jawnie wystawiony przez samą usługę. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
9. Kliknij przycisk **Zakończ** aby zakończyć pracę kreatora.  
  
     Spowoduje to utworzenie domyślny model danych, na podstawie określonej bazy danych. [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Umożliwia w celu dostosowania modelu danych. Aby uzyskać więcej informacji, zobacz [zadania](http://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Aby utworzyć usługę danych przy użyciu nowego modelu danych  
  
1.  W [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], otwórz plik edmx, który reprezentuje modelu danych.  
  
2.  W **przeglądarki modelu**, kliknij prawym przyciskiem myszy model, kliknij przycisk **właściwości**, a następnie zanotuj nazwę kontenera jednostek.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę Twojej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, a następnie kliknij przycisk **Dodaj nowy element**.  
  
4.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **usługi danych WCF**.  
  
5.  Podaj nazwę usługi, a następnie kliknij przycisk **OK**.  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]tworzy pliki znaczników i kodu XML dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu.  
  
6.  W kodzie dla usługi data, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych z typem, który dziedziczy z <xref:System.Data.Objects.ObjectContext> klasy i który jest kontenera jednostek w modelu danych, który został zapisany w kroku 2.  
  
7.  W kodzie dla usługi data Włącz autoryzowanym klientom dostęp zestawów jednostek usługa ujawnia danych. Aby uzyskać więcej informacji, zobacz [Tworzenie usługi danych](../../../../docs/framework/data/wcf/creating-the-data-service.md).  
  
8.  Aby przetestować usługę Northwind.svc danych za pomocą przeglądarki sieci Web, postępuj zgodnie z instrukcjami w temacie [uzyskiwania dostępu do usługi z przeglądarką sieci Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Instrukcje: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Instrukcje: Tworzenie usługi danych przy użyciu źródła danych LINQ to SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
