---
title: Szablony programu Visual Studio na potrzeby programu WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 13183ad5f05350c34eebd025eca3faa7d97644f8
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608026"
---
# <a name="wcf-visual-studio-templates"></a>Szablony programu Visual Studio na potrzeby programu WCF
Szablony programu Visual Studio programu Windows Communication Foundation (WCF) są wstępnie zdefiniowanymi szablonami projektów i elementów, których można używać w programie Visual Studio do szybkiego tworzenia usług WCF i otaczających aplikacji.  
  
## <a name="using-the-wcf-templates"></a>Korzystanie z szablonów WCF  
 Szablony WCF Visual Studio zapewniają podstawową strukturę klasy dla tworzenia usług. W szczególności te szablony zapewniają podstawowe definicje umowy serwisowej, umowy o dane, implementacji usługi i konfiguracji. Za pomocą tych szablonów można utworzyć prostą usługę z minimalną interakcją kodu, a także blok konstrukcyjny dla bardziej zaawansowanych usług.  
  
### <a name="wcf-service-library-project-template"></a>Szablon projektu biblioteki usług WCF  
 Szablon projektu Biblioteki usług WCF jest dostępny w oknie dialogowym nowego projektu w obszarze **Visual C#\WCF** i **Visual Basic\WCF**.  
  
 Podczas tworzenia nowego projektu przy użyciu szablonu **usługi WCF** nowy projekt automatycznie zawiera następujące trzy pliki:  
  
- Plik umowy serwisowej (IService1.cs lub IService1.vb). Plik umowy serwisowej jest interfejsem, który ma atrybuty usługi WCF zastosowane. Ten plik zawiera definicję prostej usługi, aby pokazać, jak zdefiniować usługi i zawiera operacje oparte na parametrach i przykład umowy proste dane. Jest to plik domyślny wyświetlany w edytorze kodu po utworzeniu projektu usługi WCF.  
  
- Plik implementacji usługi (Service1.cs lub Service1.vb). Plik implementacji usługi implementuje kontrakt zdefiniowany w pliku umowy serwisowej.  
  
- Plik konfiguracji aplikacji (App.config). Plik konfiguracyjny zawiera podstawowe elementy modelu usługi WCF z bezpiecznym powiązaniem HTTP. Zawiera również punkt końcowy dla usługi i umożliwia wymianę metadanych.  
  
> [!NOTE]
> Visual Studio jest skonfigurowany do rozpoznawania pliku App.config jako pliku konfiguracyjnego dla projektu, gdy jest uruchamiany przy użyciu [hosta usługi WCF (WcfSvcHost.exe),](wcf-service-host-wcfsvchost-exe.md)który jest konfiguracją domyślną. Jeśli biblioteka usług jest hostować w pliku wykonywalnym, musisz przenieść kod konfiguracji do pliku konfiguracyjnego pliku wykonywalnego, ponieważ pliki konfiguracyjne bibliotek DLL są nieprawidłowe.  
  
### <a name="wcf-service-application-template"></a>Szablon aplikacji usługi WCF  
 Szablon aplikacji usługi WCF jest dostępny w oknie dialogowym Nowy projekt w obszarze **Visual C#\WCF** i **Visual Basic\WCF**.  
  
 Podczas tworzenia nowego projektu przy użyciu szablonu **usługi aplikacji sieci Web WCF** projekt zawiera następujące cztery pliki:  
  
- Plik hosta usługi (service1.svc).  
  
- Plik umowy serwisowej (IService1.cs lub IService1.vb).  
  
- Plik implementacji usługi (Service1.svc.cs lub Service1.svc.vb).  
  
- Plik konfiguracji sieci Web (Web.config).  
  
 Szablon automatycznie tworzy witrynę sieci Web (do wdrożenia w katalogu wirtualnym) i hostuje w niej usługę.  
  
### <a name="wcf-web-site-template"></a>Szablon witryny sieci Web WCF  
 Szablon witryny sieci Web WCF jest dostępny w oknie dialogowym Nowy projekt w obszarze **Visual C#\Site\Web Service** i **Visual Basic\Web Site\WCF Service**. Spowoduje to utworzenie tych samych plików co szablon aplikacji usługi WCF, ale organizuje je tak, jakby była ASP.NET witryną sieci Web. tworzone są App_Code i App_Data foldery.  
  
### <a name="wcf-service-item-template"></a>Szablon przedmiotu serwisu WCF  
 Szablon przedmiotu serwisu WCF jest szablonem niestandardowym, który zapewnia szybki sposób dodawania usług WCF do istniejących projektów programu Visual Studio.  
  
 Aby użyć tego szablonu, przejdź do okienka **Eksplorator rozwiązań,** kliknij prawym przyciskiem myszy nazwę projektu, wskaż polecenie **Dodaj**, a następnie kliknij polecenie **Nowy element,** aby uruchomić okno dialogowe **Dodawanie nowego elementu.**  
  
 Interfejs usługi i pliki implementacji są umieszczane w głównym folderze projektu.  
  
 Szablon próbuje scalić sekcję konfiguracji nowej usługi z istniejącym plikiem konfiguracyjnym, jeśli są one zgodne typy.  
  
 Plik hosta usługi (service1.svc) jest również tworzony, jeśli istniejący projekt jest projektem sieci Web.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF Service Project i szablon elementu.  
 Szablony te tworzą usługi WCF, które obsługują usługę przepływu pracy, która jest przepływem pracy, który można uzyskać dostęp jak usługa sieci web. Istnieją oddzielne szablony dla modeli XAML lub programowania imperatywnego. Za pomocą szablonów można utworzyć sekwencyjny lub stan przepływu pracy maszyny. Aby uzyskać więcej informacji na temat tych typów przepływu pracy, zobacz [Jak: Tworzenie przepływu pracy](../windows-workflow-foundation/how-to-create-a-workflow.md). Aby uzyskać więcej informacji na temat tworzenia projektów przepływu pracy, zobacz [Tworzenie starszych projektów przepływu pracy](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer).  
  
 Visual Studio projektant jest bardziej responsywny, gdy przepływy pracy typu XOML są używane zamiast tych opartych na kodzie. Przepływ pracy XOML jest domyślnym typem przepływu pracy, który ma zostać utworzony.  
  
### <a name="wcf-syndication-service-library-template"></a>Szablon biblioteki usługi syndykacji WCF  
 Ten szablon umożliwia uwidacznianie kanału informacyjnego w formacie RSS lub ATOM jako usługi WCF. Aby uzyskać więcej informacji, zobacz [WCF Syndication](./feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Zmiana adresu kanału informacyjnego  
 Szablon syndykacji używa programu Internet Explorer podczas wykonywania. Po kliknięciu prawym przyciskiem myszy projektu w **Eksploratorze rozwiązań** w programie Visual Studio wybierz pozycję **Właściwości**, a następnie wybierz kartę **Debugowanie** i zobaczysz domyślny adres szablonu. Program Internet Explorer próbuje otworzyć kanał informacyjny pod tym adresem.  
  
 Jeśli zmienisz adres pliku danych, musisz również zmienić adres na karcie **Debugowanie.** Jeśli tego nie zrobisz, program Internet Explorer spróbuje otworzyć kanał informacyjny pod adresem domyślnym i zakończyć się niepowodzeniem.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Ajax włączony szablon przedmiotu serwisu WCF  
 Ten szablon udostępnia ajax kontroli jako usługa WCF. Aby uzyskać więcej informacji na temat formantów AJAX, zobacz [dokumentację sterowania AJAX](/aspnet/ajax/).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Szablon przedmiotu serwisu WCF z obsługą technologii Silverlight  
 Ten szablon tworzy usługę sieci Web, która dostarcza dane klientowi lub front-endowi silverlight. Szablon można dodać do witryny sieci Web lub projektu aplikacji sieci Web, aby utworzyć usługę WCF, która obejmuje kod usługi i konfigurację, które obsługują komunikację z klientem silverlight. Następnie można użyć dodaj odwołanie do **usługi,** aby dodać serwer proxy klienta usługi do klienta i wymienić dane między klientem Silverlight a usługą WCF z włączoną funkcją Silverlight.  
  
 Aby uzyskać dostęp do tego szablonu, kliknij prawym przyciskiem myszy witrynę sieci Web lub projekt aplikacji sieci Web w **Eksploratorze rozwiązań,** kliknij polecenie **Dodaj nowy element**i kliknij polecenie Usługa **WCF z włączoną funkcją Silverlight**.  
  
> [!NOTE]
> Usługa WCF obsługująca technologię `basicHttpBinding` Silverlight udostępnia punkt końcowy bez włączania żadnych ustawień zabezpieczeń. W związku z tym informacje o usłudze mogą być uzyskane przez wszystkich klientów, którzy łączą się z tą usługą. Wiadomości wymieniane między usługą a klientem również nie są podpisane ani zaszyfrowane. Aby prawidłowo zabezpieczyć punkt końcowy, należy użyć uwierzytelniania ASP.NET, HTTPS lub innych mechanizmów.  
  
## <a name="see-also"></a>Zobacz też

- [Host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Testowy klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
