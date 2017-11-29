---
title: Szablony programu Visual Studio na potrzeby programu WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a659fa3801d52da4fa4837b7df4fea9e4ac6cf5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-visual-studio-templates"></a>Szablony programu Visual Studio na potrzeby programu WCF
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] szablony są wstępnie zdefiniowanych szablonów projektów i elementów można użyć w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] można szybko utworzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi i aplikacje otaczającego.  
  
## <a name="using-the-wcf-templates"></a>Korzystanie z szablonów usługi WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Szablony zapewniają strukturę klasa podstawowa dla rozwoju usługi. W szczególności te szablony stanowią podstawowe definicje dla kontraktu usługi, kontrakt danych implementacji usługi i konfiguracji. Te szablony umożliwia tworzenie prostych usługi za pomocą kodu minimalnej interakcji, a także bloku konstrukcyjnego dla bardziej zaawansowanych usług.  
  
### <a name="wcf-service-library-project-template"></a>Szablon projektu biblioteki usługi WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Szablon projektu biblioteki usługi jest dostępna w oknie dialogowym nowego projektu w obszarze **Visual C# \WCF** i **Visual Basic\WCF**.  
  
 Podczas tworzenia nowego projektu przy użyciu **usługi WCF** szablon, nowy projekt automatycznie obejmuje trzy następujące pliki:  
  
-   Plik kontraktu usługi (IService1.cs lub IService1.vb). Plik kontraktu usługi jest interfejs, który ma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi atrybuty zastosowane. Ten plik zawiera definicję usługi simple pokazano sposób definiowania usługi oraz operacje oparte o parametry i przykładowych kontraktu danych proste. Jest to domyślny plik wyświetlany w edytorze kodu po utworzeniu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu usługi.  
  
-   Plik implementacji usługi (Service1.cs lub Service1.vb). Plik implementacji usługi implementuje kontrakt zdefiniowany w pliku kontraktu usługi.  
  
-   Plik konfiguracji aplikacji (App.config). Plik konfiguracji zawiera podstawowe elementy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelu usługi z bezpiecznego powiązania protokołu HTTP. Ponadto zawiera punkt końcowy usługi i umożliwia wymiany metadanych.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]jest skonfigurowany do rozpoznawania pliku App.config jako pliku konfiguracji dla projektu po jego uruchomieniu przy użyciu [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md), który jest konfiguracja domyślna. Jeśli na serwerze biblioteki usługi w pliku wykonywalnego, należy przenieść kod konfiguracji do pliku konfiguracyjnego pliku wykonywalnego, jak pliki konfiguracji dla bibliotek DLL są nieprawidłowe.  
  
### <a name="wcf-service-application-template"></a>Szablon aplikacji usługi WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Szablon aplikacji usługi jest dostępny w oknie dialogowym Nowy projekt w obszarze **Visual C# \WCF** i **Visual Basic\WCF**.  
  
 Podczas tworzenia nowego projektu przy użyciu **usługi aplikacji sieci Web WCF** szablon projektu zawiera cztery następujące pliki:  
  
-   Plik hosta usługi (plik service1.svc).  
  
-   Plik kontraktu usługi (IService1.cs lub IService1.vb).  
  
-   Plik implementacji usługi (Service1.svc.cs lub Service1.svc.vb).  
  
-   Plik konfiguracji sieci Web (Web.config).  
  
 Szablon automatycznie tworzy witryny sieci Web (w celu wdrażania na katalog wirtualny) i obsługuje usługę w nim.  
  
### <a name="wcf-web-site-template"></a>Szablon witryny sieci Web WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Szablon witryny sieci Web jest dostępna w oknie dialogowym Nowy projekt w obszarze **Visual C# \Web Site\WCF usługi** i **Visual usługi Site\WCF Basic\Web**. Tworzy tych samych plików jako szablon aplikacji usługi WCF, ale organizuje je tak, jakby była witryny sieci web ASP.NET. Są tworzone foldery App_Code i App_Data.  
  
### <a name="wcf-service-item-template"></a>Szablon elementu Usługa WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Szablonu elementu Service jest szablon niestandardowy, który umożliwia szybkie, aby dodać [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services do istniejącej [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] projektów.  
  
 Aby użyć tego szablonu, przejdź do **Eksploratora rozwiązań** okienku kliknij prawym przyciskiem myszy nazwę projektu, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **nowy element** można uruchomić **Dodaj nowy Element** okno dialogowe.  
  
 Pliki interfejsu i implementacji usługi są umieszczane w folderze głównym projektu.  
  
 Szablon próbuje scalić sekcji konfiguracji nową usługę do istniejącego pliku konfiguracji, jeśli są one niezgodne typy.  
  
 Pliku hosta usługi (plik service1.svc) również jest tworzony, jeśli istniejący projekt jest projektem sieci Web.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Projekt WF usługi WCF i szablon elementu.  
 Te szablony tworzą [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi przepływu pracy, jaką jest przepływ pracy, który można uzyskać dostępu do usługi, takich jak usługi sieci web. Szablony oddzielne istnieje XAML i imperatywnych modelach programowania. Korzystanie z szablonów, można utworzyć przepływ pracy automatu Sekwencyjna lub stanu. Aby uzyskać więcej informacji o tych typach przepływu pracy, zobacz [Windows Workflow Foundation samouczki](http://msdn.microsoft.com/en-us/e9705654-bd96-4b56-8d98-f1f118112d97). [!INCLUDE[crabout](../../../includes/crabout-md.md)]Tworzenie projektów przepływu pracy, zobacz [tworzenia projektów przepływu pracy starszego](/visualstudio/workflow-designer/creating-legacy-workflow-projects).  
  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]Projektant jest bardziej elastyczny, gdy typ XOML, przepływy pracy są używane zamiast tego kodu na podstawie tych. XOML przepływu pracy jest domyślny typ przepływu pracy do utworzenia.  
  
### <a name="wcf-syndication-service-library-template"></a>Szablon biblioteki usługi syndykacji WCF  
 Ten szablon umożliwia narazić Twoje źródła danych w formacie RSS lub ATOM jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi. Aby uzyskać więcej informacji, zobacz [syndykacji WCF](../../../docs/framework/wcf/feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Zmiana adresu źródła danych  
 Szablon zespolonego używa programu Internet Explorer podczas wykonywania. Po kliknięciu prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], wybierz pozycję **właściwości**, a następnie wybierz pozycję **debugowania** kartę, aby sprawdzić adres domyślnej szablon. Program Internet Explorer próbuje otworzyć kanału informacyjnego pod tym adresem.  
  
 Jeśli zmienisz adres Twojego źródła danych, należy również zmienić adres w **debugowania** kartę. Jeśli nie zrobisz, Internet Explorer próby otwarcia kanału informacyjnego pod domyślnym adresem i zakończyć się niepowodzeniem.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Szablon elementu Usługa WCF z włączoną technologii AJAX  
 Ten szablon udostępnia kontrolkę technologii AJAX jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi. Aby uzyskać więcej informacji na formanty interfejsu AJAX, zobacz [AJAX kontroli dokumentacji](http://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Szablon elementu Usługa WCF z włączoną obsługą technologii Silverlight  
 Ten szablon umożliwia tworzenie usługi sieci Web, która dostarcza dane do klienta Silverlight lub frontonu. Szablon można dodać do projektu aplikacji witryny sieci Web lub aplikacji internetowej można utworzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi, która zawiera kod usługi i konfigurację, która obsługuje komunikację z klientem programu Silverlight. Następnie można użyć **Dodaj odwołanie do usługi** dodanie usługi serwera proxy klienta do klienta, a wymiany danych między klientem programu Silverlight i usługi WCF z włączoną obsługą technologii Silverlight.  
  
 Aby uzyskać dostęp do tego szablonu, kliknij prawym przyciskiem myszy projekt aplikacji witryny sieci Web lub aplikacji internetowej w **Eksploratora rozwiązań**, kliknij przycisk **Dodaj nowy element**i kliknij przycisk **obsługującą program Silverlight usługi WCF**.  
  
> [!NOTE]
>  Udostępnia usługi WCF obsługującą program Silverlight `basicHttpBinding` punktu końcowego bez włączania wszelkich ustawień zabezpieczeń. W związku z tym można uzyskać informacji o usłudze przez wszystkich klientów łączących się z tą usługą. Wiadomości wymieniane między usługą i klienta nie jest podpisana lub zaszyfrowana. Aby właściwie zabezpieczyć punktu końcowego, należy używać uwierzytelniania programu ASP.NET, HTTPS lub innych mechanizmów.  
  
## <a name="see-also"></a>Zobacz też  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Klienta testowego WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
