---
title: Szablony programu Visual Studio na potrzeby programu WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 1b4a600e4ed19b967bcaeb6d880ea181b7c2d61f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197194"
---
# <a name="wcf-visual-studio-templates"></a>Szablony programu Visual Studio na potrzeby programu WCF
Windows Communication Foundation (WCF) szablony programu Visual Studio są wstępnie zdefiniowanymi szablonami projektu i elementów, których można użyć w programie Visual Studio, aby szybko tworzyć usługi WCF i otaczające aplikacje.  
  
## <a name="using-the-wcf-templates"></a>Korzystanie z szablonów WCF  
 Szablony Visual Studio programu WCF zapewniają podstawową strukturę klasy do tworzenia usług. Szablony te zawierają podstawowe definicje kontraktu usług, kontraktu danych, implementacji usługi i konfiguracji. Za pomocą tych szablonów można utworzyć prostą usługę z minimalnym interakcją kodu, a także blok konstrukcyjny dla bardziej zaawansowanych usług.  
  
### <a name="wcf-service-library-project-template"></a>Szablon projektu biblioteki usługi WCF  
 Szablon projektu biblioteki usług WCF jest dostępny w oknie dialogowym Nowy projekt w obszarze **Visual C#\WCF** i **Visual Basic\WCF**.  
  
 Podczas tworzenia nowego projektu przy użyciu szablonu **usługi WCF** nowy projekt automatycznie zawiera następujące trzy pliki:  
  
- Plik kontraktu usługi (IService1.cs lub IService1. vb). Plik kontraktu usługi jest interfejsem, który ma zastosowane atrybuty usługi WCF. Ten plik zawiera definicję prostej usługi, która pokazuje, jak definiować usługi, i zawiera operacje oparte na parametrach oraz prostej umowie dotyczącej danych. Jest to domyślny plik wyświetlany w edytorze kodu po utworzeniu projektu usługi WCF.  
  
- Plik implementacji usługi (Service1.cs lub Service1. vb). Plik implementacji usługi implementuje kontrakt zdefiniowany w pliku kontraktu usługi.  
  
- Plik konfiguracji aplikacji (App. config). Plik konfiguracji zawiera podstawowe elementy modelu usługi WCF z bezpiecznym powiązaniem HTTP. Zawiera również punkt końcowy usługi i umożliwia wymianę metadanych.  
  
> [!NOTE]
> Program Visual Studio jest skonfigurowany do rozpoznawania pliku App. config jako plik konfiguracji projektu, gdy jest uruchamiany przy użyciu [hosta usługi WCF (WcfSvcHost. exe)](wcf-service-host-wcfsvchost-exe.md), który jest domyślną konfiguracją. Jeśli Biblioteka usług jest hostowana w pliku wykonywalnym, należy przenieść kod konfiguracji do pliku konfiguracyjnego pliku wykonywalnego, ponieważ pliki konfiguracji bibliotek DLL są nieprawidłowe.  
  
### <a name="wcf-service-application-template"></a>Szablon aplikacji usługi WCF  
 Szablon aplikacji usługi WCF jest dostępny w oknie dialogowym Nowy projekt w obszarze **Visual C#\WCF** i **Visual Basic\WCF**.  
  
 Podczas tworzenia nowego projektu przy użyciu szablonu **usługi aplikacji sieci Web programu WCF** projekt zawiera następujące cztery pliki:  
  
- Plik hosta usługi (Service1. svc).  
  
- Plik kontraktu usługi (IService1.cs lub IService1. vb).  
  
- Plik implementacji usługi (Service1.svc.cs lub Service1. svc. vb).  
  
- Plik konfiguracji sieci Web (Web. config).  
  
 Szablon automatycznie tworzy witrynę sieci Web (do wdrożenia w katalogu wirtualnym) i hostuje w niej usługę.  
  
### <a name="wcf-web-site-template"></a>Szablon witryny sieci Web WCF  
 Szablon witryny sieci Web WCF jest dostępny w oknie dialogowym Nowy projekt w obszarze **Visual C#\Serwer sieci Site\WCF Service** i **Visual Basic\Web Site\WCF Service**. Spowoduje to utworzenie takich samych plików jak szablon aplikacji usługi WCF, ale organizuje je tak, jakby była witryną sieci Web ASP.NET. Tworzone są foldery App_Code i App_Data.  
  
### <a name="wcf-service-item-template"></a>Szablon elementu usługi WCF  
 Szablon elementu usługi WCF jest szablonem niestandardowym, który umożliwia szybkie dodawanie usług WCF do istniejących projektów programu Visual Studio.  
  
 Aby użyć tego szablonu, przejdź do okienka **Eksplorator rozwiązań** , kliknij prawym przyciskiem myszy nazwę projektu, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **nowy element** , aby uruchomić okno dialogowe **Dodaj nowy element** .  
  
 Interfejs usługi i pliki implementacji są umieszczane w folderze głównym projektu.  
  
 Szablon podejmuje próbę scalenia sekcji konfiguracji nowej usługi z istniejącym plikiem konfiguracji, jeśli są one zgodne z typami.  
  
 Plik hosta usługi (Service1. svc) jest również tworzony, jeśli istniejący projekt jest projektem sieci Web.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Projekt usługi WCF WF i szablon elementu.  
 Te szablony tworzą usługi WCF obsługujące usługę przepływu pracy, która jest przepływem pracy, który można uzyskać dostęp do usługi sieci Web. Istnieją osobne szablony dla języka XAML lub bezwzględnych modeli programistycznych. Za pomocą szablonów można utworzyć sekwencyjny przepływ pracy automatu lub stanu. Aby uzyskać więcej informacji na temat tego typu przepływu pracy, zobacz [How to: Create a Workflow](../windows-workflow-foundation/how-to-create-a-workflow.md). Aby uzyskać więcej informacji na temat tworzenia projektów przepływu pracy, zobacz [Tworzenie starszych projektów przepływu pracy](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer).  
  
 Program Visual Studio Designer jest bardziej reagujący, gdy są używane przepływy pracy typu XOML zamiast kodu. Przepływ pracy XOML jest domyślnym typem przepływu pracy, który ma zostać utworzony.  
  
### <a name="wcf-syndication-service-library-template"></a>Szablon biblioteki usługi zespalania programu WCF  
 Ten szablon umożliwia udostępnienie kanału informacyjnego w formacie RSS lub ATOM jako usługi WCF. Aby uzyskać więcej informacji, zobacz temat [zespalanie WCF](./feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Zmiana adresu kanału informacyjnego  
 Szablon zespalania używa programu Internet Explorer podczas wykonywania. Po kliknięciu prawym przyciskiem myszy projektu w **Eksploratorze rozwiązań** w programie Visual Studio wybierz pozycję **Właściwości**, a następnie wybierz kartę **debugowanie** i sprawdź, czy jest wyświetlany domyślny adres szablonu. Program Internet Explorer podejmie próbę otwarcia kanału informacyjnego pod tym adresem.  
  
 W przypadku zmiany adresu kanału informacyjnego należy również zmienić adres na karcie **debugowanie** . Jeśli tego nie zrobisz, program Internet Explorer podejmie próbę otwarcia źródła danych przy użyciu adresu domyślnego i niepowodzeniem.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Szablon elementu usługi WCF z włączoną obsługą technologii AJAX  
 Ten szablon udostępnia kontrolkę AJAX jako usługę WCF. Aby uzyskać więcej informacji na temat kontrolek AJAX, zobacz [dokumentację kontroli AJAX](https://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Szablon elementu usługi WCF z włączonym dodatkiem Silverlight  
 Ten szablon służy do tworzenia usługi sieci Web, która dostarcza dane do klienta Silverlight lub frontonu. Szablon można dodać do witryny sieci Web lub projektu aplikacji sieci Web w celu utworzenia usługi WCF, która zawiera kod i konfigurację usługi, która obsługuje komunikację z klientem Silverlight. Następnie można użyć **Dodaj odwołanie do usługi** , aby dodać klienta serwera proxy usługi do klienta i wymiany danych między klientem Silverlight a usługą WCF obsługującą program Silverlight.  
  
 Aby uzyskać dostęp do tego szablonu, kliknij prawym przyciskiem myszy witrynę sieci Web lub projekt aplikacji sieci Web w **Eksplorator rozwiązań**, kliknij przycisk **Dodaj nowy element**, a następnie kliknij pozycję **usługa WCF z włączoną obsługą Silverlight**.  
  
> [!NOTE]
> Usługa WCF z włączoną obsługą technologii Silverlight uwidacznia punkt końcowy `basicHttpBinding` bez włączania żadnych ustawień zabezpieczeń. W związku z tym informacje o usłudze mogą zostać uzyskane przez wszystkich klientów, którzy łączą się z tą usługą. Komunikaty wymieniane między usługą a klientem również nie są podpisane ani zaszyfrowane. Aby prawidłowo zabezpieczyć punkt końcowy, należy użyć uwierzytelniania ASP.NET, protokołu HTTPS lub innych mechanizmów.  
  
## <a name="see-also"></a>Zobacz także

- [Host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Testowy klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
