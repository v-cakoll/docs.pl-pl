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
manager: douge
ms.openlocfilehash: f0c760d0f9b65fc9b612a8bee8abb68fa5b4ecae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516110"
---
# <a name="service-application-programming-architecture"></a>Architektura programowania aplikacji usług
Aplikacje usług systemu Windows są oparte na klasę, która dziedziczy <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> klasy. Przesłaniaj metody z tej klasy i zdefiniuj funkcji je, aby określić sposób działania usługi.  
  
 Klasy głównym zaangażowane w tworzenie usług są:  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — Można zastąpić metody z <xref:System.ServiceProcess.ServiceBase> klasy podczas tworzenia usługi i definiują kod, aby określić, jak Usługa funkcji w tym dziedziczone klasy.  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> i <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> — te klasy służą do instalowania i odinstalowywania usługi.  
  
 Ponadto klasa o nazwie <xref:System.ServiceProcess.ServiceController> może służyć do operowania samą usługę. Ta klasa nie jest do utworzenia usługi, ale może służyć do uruchamiania i Zatrzymaj usługę, Przekaż do niego poleceń i zwracać szereg wyliczenia.  
  
## <a name="defining-your-services-behavior"></a>Definiowanie zachowania usługi  
 W klasie usługi należy zastąpić funkcje klasy podstawowej, które określają, co się dzieje, gdy stan usługi zostanie zmieniona w Menedżerze sterowania usługami. <xref:System.ServiceProcess.ServiceBase> Klasa udostępnia następujące metody, które można zmienić, aby dodać niestandardowe zachowanie.  
  
|Metoda|Zastąpienie|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Wskazuje, jakie działania należy podjąć, podczas uruchamiania usługi. W tej procedurze usługi do wykonywania pracy przydatne należy napisać kod.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Wskazuje, co powinno się zdarzyć, gdy usługa jest wstrzymana.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Wskazuje, co powinno się zdarzyć, gdy usługa przestanie działać.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Wskazuje, co powinno się zdarzyć, gdy usługa wznawia normalne działanie po wstrzymaniu.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Wskazuje, co powinno się stać wcześniejszy niż system zamykana, jeśli usługa jest uruchomiona w tym czasie.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Wskazuje, co powinno się stać z usługą odebrania polecenia niestandardowych. Aby uzyskać więcej informacji o niestandardowych poleceń Zobacz MSDN online.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Wskazuje, jak usługa powinna odpowiadać po odebraniu zdarzenie zarządzania energią, takich jak niskim poziomie naładowania baterii lub wstrzymane operacji.|  
  
> [!NOTE]
>  Te metody reprezentują stanów, które usługa przechodzi przez w jego trwania. Usługa przejść z jednego stanu do następnej. Na przykład, nigdy nie otrzymasz usługi odpowiedzieć na <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> polecenia przed <xref:System.ServiceProcess.ServiceBase.OnStart%2A> została wywołana.  
  
 Istnieje kilka innych właściwości i metod, które mogą być przydatne. Należą do nich następujące elementy:  
  
-   <xref:System.ServiceProcess.ServiceBase.Run%2A> Metoda <xref:System.ServiceProcess.ServiceBase> klasy. To jest główny punkt wejścia dla usługi. Podczas tworzenia usługi przy użyciu szablonu usług systemu Windows, kod jest wstawiany do aplikacji `Main` metody w celu uruchomienia usługi. Ten kod wygląda następująco:  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  Poniższe przykłady Użyj tablicy typu <xref:System.ServiceProcess.ServiceBase>, do którego można dodać poszczególnych usług aplikacji i wszystkich usług można uruchomić jednocześnie. Jeśli tworzysz tylko jednej usługi, jednak warto nie używają tablicy i po prostu zadeklarować nowy obiekt dziedziczenie z <xref:System.ServiceProcess.ServiceBase> , a następnie uruchom go. Na przykład zobacz [porady: programowane pisanie usług](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
-   Szereg właściwości <xref:System.ServiceProcess.ServiceBase> klasy. Te określają, jakie metody można wywołać w usłudze. Na przykład, jeśli <xref:System.ServiceProcess.ServiceBase.CanStop%2A> właściwość jest ustawiona na `true`, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> można wywołać metody w usłudze. Gdy <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> właściwość jest ustawiona na `true`, <xref:System.ServiceProcess.ServiceBase.OnPause%2A> i <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> można wywołać metody. Po określeniu jednej z tych właściwości na `true`, należy zastąpić i zdefiniuj przetwarzania dla metod skojarzone.  
  
    > [!NOTE]
    >  Co najmniej przesłonięcie usługi <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> użyteczne.  
  
 Można również użyć składnik o nazwie <xref:System.ServiceProcess.ServiceController> do komunikacji z i kontrolują zachowanie istniejącą usługę.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Instrukcje: tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
