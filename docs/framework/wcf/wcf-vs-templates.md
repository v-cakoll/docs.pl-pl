---
title: Szablony programu Visual Studio na potrzeby programu WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 2e192e671d37e096e4199b295d4f533194ab89b6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613231"
---
# <a name="wcf-visual-studio-templates"></a>Szablony programu Visual Studio na potrzeby programu WCF
Szablony programu Visual Studio Windows Communication Foundation (WCF) są wstępnie zdefiniowane szablony projektów i elementów, które w programie Visual Studio umożliwia szybkie tworzenie usług WCF i otaczającego aplikacji.  
  
## <a name="using-the-wcf-templates"></a>Za pomocą szablonów usługi WCF  
 Szablony programu Visual Studio WCF stanowią strukturę podstawowe klasy do tworzenia aplikacji usługi. W szczególności te szablony zapewniają podstawowe definicje dla kontraktu usługi, kontraktu danych, usługi wdrażania i konfiguracji. Można użyć tych szablonów, aby utworzyć prostą usługę za pomocą minimalnej ilości kodu interakcji, a także blok konstrukcyjny dla bardziej zaawansowanych usług.  
  
### <a name="wcf-service-library-project-template"></a>Szablon projektu biblioteki usługi WCF  
 Szablon projektu biblioteki usługi WCF jest dostępna w okno dialogowe Nowy projekt w obszarze **Visual C# \WCF** i **Visual Basic\WCF**.  
  
 Podczas tworzenia nowego projektu przy użyciu **usługi WCF** szablon nowego projektu automatycznie uwzględnia następujące trzy pliki:  
  
- Plik kontraktu usługi (IService1.cs lub IService1.vb). Plik kontraktu usługi jest interfejs, który został zastosowany atrybuty usługi WCF. Ten plik zawiera definicję prostą usługę, aby pokazać sposób definiowania usługi oraz operacje oparte o parametry i przykładowych kontraktu danych proste. Jest to domyślny plik wyświetlany w edytorze kodu, po utworzeniu projektu usługi WCF.  
  
- Plik implementacji usługi (Service1.cs lub Service1.vb). Plik implementacji usługi implementuje kontrakt zdefiniowany w pliku kontraktu usługi.  
  
- Plik konfiguracji aplikacji (App.config). Plik konfiguracyjny zawiera podstawowe elementy modelu usług WCF za pomocą bezpiecznego powiązania protokołu HTTP. Ponadto zawiera punkt końcowy usługi i umożliwia wymiany metadanych.  
  
> [!NOTE]
>  Program Visual Studio jest skonfigurowana do rozpoznać pliku App.config jako plik konfiguracyjny dla projektu, po uruchomieniu przy użyciu [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md), która jest domyślna konfiguracja. Jeśli na serwerze biblioteki usługi w pliku wykonywalnym, należy przenieść kod konfiguracji do pliku konfiguracyjnego pliku wykonywalnego, jak pliki konfiguracji dla bibliotek DLL nie są prawidłowe.  
  
### <a name="wcf-service-application-template"></a>Szablon aplikacja usługi WCF  
 Szablon aplikacja usługi WCF jest dostępny w oknie dialogowym Nowy projekt w obszarze **Visual C# \WCF** i **Visual Basic\WCF**.  
  
 Podczas tworzenia nowego projektu przy użyciu **usługi aplikacji sieci Web WCF** szablonu projektu obejmuje cztery następujące pliki:  
  
- Host usługi plików (plik service1.svc).  
  
- Plik kontraktu usługi (IService1.cs lub IService1.vb).  
  
- Plik implementacji usługi (Service1.svc.cs lub Service1.svc.vb).  
  
- Plik konfiguracji sieci Web (Web.config).  
  
 Szablon automatycznie tworzy witrynę sieci Web (do wdrożenia dla katalogu wirtualnego) i hostuje usługę w nim.  
  
### <a name="wcf-web-site-template"></a>Szablon witryny sieci Web WCF  
 Szablon witryny sieci Web WCF jest dostępny w oknie dialogowym Nowy projekt w obszarze **Visual C# \Web Site\WCF usługi** i **usługi Site\WCF Basic\Web Visual**. Tworzy te same pliki jako szablon aplikacja usługi WCF, ale organizuje je tak, jakby był to witryna sieci web ASP.NET. App_Code oraz App_Data foldery będą tworzone.  
  
### <a name="wcf-service-item-template"></a>Szablon elementu Usługa WCF  
 Szablon elementu Usługa WCF jest szablon niestandardowy, który zapewnia szybki sposób nad dodaniem usług WCF do istniejących projektów programu Visual Studio.  
  
 Aby użyć tego szablonu, przejdź do **Eksploratora rozwiązań** okienku kliknij prawym przyciskiem myszy nazwę projektu, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy element** można uruchomić **Dodaj nowe Element** okno dialogowe.  
  
 Pliki interfejsu i implementacji usługi są umieszczane w folderze głównym projektu.  
  
 Szablon próbuje scalić sekcji konfiguracji nową usługę, która istniejący plik konfiguracyjny, jeśli są one niezgodne typy.  
  
 Pliku hosta usługi (plik service1.svc) jest tworzona, jeśli istniejący projekt jest projektem sieci Web.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Projekt programu WF usługi WCF i szablon elementu.  
 Te szablony tworzą usług WCF tego hosta usługi przepływu pracy, który jest przepływ pracy, który można uzyskać dostęp, takich jak usługi sieci web. Istnieje osobnymi szablonami XAML i imperatywnego modelach programowania. Korzystanie z szablonów, można utworzyć przepływ pracy automatu Sekwencyjna lub stanu. Aby uzyskać więcej informacji na temat tego rodzaju przepływu pracy, zobacz [jak: Tworzenie przepływu pracy](../windows-workflow-foundation/how-to-create-a-workflow.md). Aby uzyskać więcej informacji na temat tworzenia projektów przepływu pracy, zobacz [tworzenie starszej wersji projektów przepływu pracy](/visualstudio/workflow-designer/creating-legacy-workflow-projects).  
  
 Projektanta Visual Studio jest bardziej reaktywny, gdy typ XOML, przepływy pracy są używane zamiast tego kodu na podstawie tych. XOML przepływu pracy jest domyślny typ przepływu pracy, który ma zostać utworzony.  
  
### <a name="wcf-syndication-service-library-template"></a>Szablon Biblioteka usługi syndykacji WCF  
 Ten szablon umożliwia udostępnianie Twoje źródło danych w formacie takich jak usługi WCF. Aby uzyskać więcej informacji, zobacz [syndykacja programu WCF](../../../docs/framework/wcf/feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Zmiana adresu kanału informacyjnego  
 Szablon syndykacji używa programu Internet Explorer podczas wykonywania. Po kliknięciu prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierz **właściwości**, a następnie wybierz **debugowania** kartę, aby sprawdzić adres domyślny szablon. Program Internet Explorer próbuje otworzyć źródło danych pod tym adresem.  
  
 Jeśli zmienisz adres Twoje źródło danych, należy zmienić adres w **debugowania** kartę. Jeśli nie zrobisz, program Internet Explorer próbuje Otwórz źródło danych pod domyślnym adresem i zakończyć się niepowodzeniem.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Szablon elementu Usługa WCF z włączoną technologii AJAX  
 Ten szablon przedstawia kontrolka AJAX jako usługa WCF. Aby uzyskać więcej informacji na temat kontrolek AJAX, zobacz [dokumentacji dotyczącej kontroli AJAX](https://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Szablon elementu Usługa WCF z włączoną obsługą technologii Silverlight  
 Ten szablon tworzy usługi sieci Web, który dostarcza dane do klienta Silverlight lub frontonu. Szablon można dodać do witryny sieci Web lub sieci Web projektu aplikacji do tworzenia usługi WCF, który zawiera kod usługi i konfigurację, która obsługuje komunikację z klientem programu Silverlight. Następnie można użyć **Dodaj odwołanie do usługi** Dodaj usługi Serwer proxy klienta do klienta w celu wymiany danych między klientem programu Silverlight i usługi WCF z włączoną obsługą technologii Silverlight.  
  
 Aby uzyskać dostęp do tego szablonu, kliknij prawym przyciskiem myszy projekt aplikacji witryny sieci Web lub sieci Web w **Eksploratora rozwiązań**, kliknij przycisk **Dodaj nowy element**i kliknij przycisk **usługi WCF obsługującej program Silverlight**.  
  
> [!NOTE]
>  Usługa WCF obsługująca program Silverlight przedstawia `basicHttpBinding` punktu końcowego bez włączania wszelkich ustawień zabezpieczeń. W związku z tym można uzyskać informacji na temat usługi przez wszystkich klientów łączących się z tej usługi. Komunikatów wymienianych między usługą i klienta również nie jest podpisana lub zaszyfrowana. Aby zabezpieczyć punkt końcowy prawidłowo, należy użyć uwierzytelniania platformy ASP.NET, HTTPS lub innych mechanizmów.  
  
## <a name="see-also"></a>Zobacz także

- [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
