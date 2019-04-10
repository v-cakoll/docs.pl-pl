---
title: Architektura programowania aplikacji usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
author: ghogen
ms.openlocfilehash: 17e16cec34b381cdfe46e1066c3219a93c3780e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216395"
---
# <a name="service-application-programming-architecture"></a>Architektura programowania aplikacji usług
Aplikacje usług Windows opierają się na klasę, która dziedziczy po elemencie <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> klasy. Przesłaniaj metody z tej klasy i zdefiniować funkcje dla nich określić sposób działania usługi.  
  
 Dostępne są następujące główne klasy związane z tworzenia usługi:  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — Można zastąpić metody z <xref:System.ServiceProcess.ServiceBase> klasy podczas tworzenia usługi i definiują kod w celu określenia, jak w tym funkcji usługi dziedziczone klasy.  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> i <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> — klasy te służą do instalowania i odinstalowywania usługi.  
  
 Ponadto, klasę o nazwie <xref:System.ServiceProcess.ServiceController> może służyć do manipulowania samą usługę. Ta klasa nie jest do utworzenia usługi, ale może służyć do uruchamiania i Zatrzymaj usługę, Przekaż do niego poleceń i zwracać szereg wyliczenia.  
  
## <a name="defining-your-services-behavior"></a>Definiowanie zachowania usługi  
 W klasie usługi, możesz przesłonić funkcji klasy podstawowej, które określają, co się stanie, gdy stan usługi zostanie zmieniona w Menedżerze kontroli usług. <xref:System.ServiceProcess.ServiceBase> Klasa udostępnia następujące metody, które można przesłonić, aby dodać zachowanie niestandardowe.  
  
|Metoda|Należy przesłonić, aby|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Wskazuje, jakie działania powinny zostać podjęte, gdy usługa zacznie działać. W ramach tej procedury dla usługi w celu wykonywania użytecznej pracy, należy napisać kod.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Wskazuje, co ma się zdarzyć, gdy usługa jest wstrzymana.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Wskazuje, co ma się zdarzyć, gdy usługa przestanie działać.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Wskazuje, co ma się zdarzyć, gdy usługa wznawia normalnego funkcjonowania po wstrzymaniu.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Wskazuje, co ma się zdarzyć tuż przed systemem, zamykanie, jeśli usługa jest uruchomiona w danym momencie.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Wskazuje, co ma się zdarzyć, gdy usługa odbiera polecenie niestandardowe. Aby uzyskać więcej informacji na temat niestandardowych poleceń zobacz artykuł MSDN w trybie online.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Wskazuje, jak usługa powinien odpowiadać po otrzymaniu zdarzenie zarządzania energią, takich jak niskiego poziomu baterii lub operacja wstrzymana.|  
  
> [!NOTE]
>  Metody te reprezentują stanów, które usługa przechodzi przez w jego trwania. Usługa przejścia z jednego stanu do drugiego. Na przykład, nigdy nie uzyskasz usługę, aby odpowiedzieć na <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> polecenia przed <xref:System.ServiceProcess.ServiceBase.OnStart%2A> została wywołana.  
  
 Istnieje kilka innych właściwości i metod, które są przedmiotem zainteresowania. Należą do nich następujące elementy:  
  
-   <xref:System.ServiceProcess.ServiceBase.Run%2A> Metody <xref:System.ServiceProcess.ServiceBase> klasy. To jest główny punkt wejścia dla usługi. Podczas tworzenia usługi przy użyciu szablonu usługi Windows kod jest wstawiany do aplikacji `Main` metodę, aby uruchomić usługę. Ten kod wygląda następująco:  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  Te przykłady skorzystaj z tablicy typu <xref:System.ServiceProcess.ServiceBase>, w którym można dodać usługę, każda aplikacja zawiera i następnie wszystkich usług mogą być uruchamiane jednocześnie. Jeśli tworzysz tylko jednej usługi, jednak może nie chcesz używać tablicy i po prostu Zadeklaruj nowy obiekt, który dziedziczy z <xref:System.ServiceProcess.ServiceBase> , a następnie uruchom go. Aby uzyskać przykład, zobacz [jak: Programowane pisanie usług](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
-   Szereg właściwości <xref:System.ServiceProcess.ServiceBase> klasy. Te określają, jakie metody można wywołać w Twojej usłudze. Na przykład, gdy <xref:System.ServiceProcess.ServiceBase.CanStop%2A> właściwość jest ustawiona na `true`, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> można wywołać metody dla Twojej usługi. Gdy <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> właściwość jest ustawiona na `true`, <xref:System.ServiceProcess.ServiceBase.OnPause%2A> i <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> można wywołać metody. Po ustawieniu jednej z tych właściwości, aby `true`, należy zastąpić i zdefiniować przetwarzanie skojarzone metod.  
  
    > [!NOTE]
    >  Usługi muszą przesłaniać co najmniej <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> były przydatne.  
  
 Możesz również użyć składnik o nazwie <xref:System.ServiceProcess.ServiceController> komunikuje się z i kontrolowania zachowania istniejącej usługi.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Instrukcje: Tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
