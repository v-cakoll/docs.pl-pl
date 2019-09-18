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
ms.openlocfilehash: 1c197b487f1cb7596f507f663fe3f1fb83857cbd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053488"
---
# <a name="service-application-programming-architecture"></a>Architektura programowania aplikacji usług
Aplikacje usług systemu Windows są oparte na klasie, która dziedziczy z <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> klasy. Zastąpisz metody z tej klasy i zdefiniujesz dla nich funkcję, aby określić sposób zachowania usługi.  
  
 Główne klasy wykorzystywane podczas tworzenia usług są następujące:  
  
- <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>— Przesłonięcia metod z <xref:System.ServiceProcess.ServiceBase> klasy podczas tworzenia usługi i definiowania kodu w celu określenia sposobu działania usługi w tej dziedziczonej klasie.  
  
- <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType>i <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> — te klasy są używane do instalowania i odinstalowywania usługi.  
  
 Ponadto klasy o nazwie <xref:System.ServiceProcess.ServiceController> można użyć do manipulowania samą usługą. Ta klasa nie obejmuje tworzenia usługi, ale może służyć do uruchamiania i zatrzymywania usługi, przekazywania do niej poleceń i zwracania serii wyliczeń.  
  
## <a name="defining-your-services-behavior"></a>Definiowanie zachowania usługi  
 W klasie usług przesłonisz funkcje klasy podstawowej, które określają, co się stanie w przypadku zmiany stanu usługi w Menedżerze kontroli usług. <xref:System.ServiceProcess.ServiceBase> Klasa uwidacznia następujące metody, które można przesłonić w celu dodania zachowania niestandardowego.  
  
|Metoda|Przesłoń do|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Wskaż, jakie akcje należy wykonać, gdy usługa zostanie uruchomiona. Musisz napisać kod w tej procedurze, aby usługa mogła wykonywać przydatne działania.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Wskaż, co się dzieje, gdy usługa jest wstrzymana.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Wskaż, co się dzieje, gdy usługa przestanie działać.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Wskaż, co się dzieje, gdy usługa wznawia normalne działanie po jego wstrzymaniu.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Wskaż, co się dzieje tuż przed zamknięciem systemu, jeśli usługa jest uruchomiona w tym czasie.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Wskaż, co się dzieje, gdy usługa odbierze polecenie niestandardowe. Aby uzyskać więcej informacji na temat poleceń niestandardowych, zobacz MSDN Online.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Wskaż, w jaki sposób usługa powinna reagować po odebraniu zdarzenia zarządzania zasilaniem, na przykład w przypadku niskiej baterii lub wstrzymanej operacji.|  
  
> [!NOTE]
> Te metody reprezentują Stany przenoszone przez usługę w jego okresie istnienia; przejście usługi z jednego stanu do następnego. Na przykład usługa nie będzie mogła odpowiedzieć na <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> polecenie przed <xref:System.ServiceProcess.ServiceBase.OnStart%2A> wywołaniem.  
  
 Istnieje kilka innych właściwości i metod, które są interesujące. Należą do nich następujące elementy:  
  
- <xref:System.ServiceProcess.ServiceBase.Run%2A> Metoda<xref:System.ServiceProcess.ServiceBase> klasy. To jest główny punkt wejścia dla usługi. Podczas tworzenia usługi przy użyciu szablonu usługi systemu Windows kod jest wstawiany w `Main` metodzie aplikacji, aby uruchomić usługę. Ten kod wygląda następująco:  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    > W tych przykładach użyto tablicy typu <xref:System.ServiceProcess.ServiceBase>, w którym można dodać każdą usługę, która zawiera daną aplikację, a następnie można uruchomić wszystkie usługi jednocześnie. Jeśli jednak tworzysz tylko jedną usługę, możesz zrezygnować z używania tablicy i po prostu zadeklarować nowy obiekt Dziedziczony z <xref:System.ServiceProcess.ServiceBase> , a następnie uruchomić go. Aby zapoznać się z przykładem, zobacz [How to: Programowo](how-to-write-services-programmatically.md)pisać usługi.  
  
- Seria właściwości <xref:System.ServiceProcess.ServiceBase> klasy. Określają metody, które można wywołać w usłudze. Na przykład, gdy <xref:System.ServiceProcess.ServiceBase.CanStop%2A> właściwość jest ustawiona na `true`, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> Metoda w usłudze może być wywoływana. Gdy właściwość jest ustawiona na `true`, <xref:System.ServiceProcess.ServiceBase.OnPause%2A> metody i <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> mogą być wywoływane. <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> Po ustawieniu jednej z tych właściwości na `true`, należy zastąpić i zdefiniować przetwarzanie dla skojarzonych metod.  
  
    > [!NOTE]
    > Usługa musi przesłonić co <xref:System.ServiceProcess.ServiceBase.OnStart%2A> najmniej <xref:System.ServiceProcess.ServiceBase.OnStop%2A> i być przydatne.  
  
 Można również użyć składnika o nazwie, <xref:System.ServiceProcess.ServiceController> aby komunikować się i kontrolować zachowanie istniejącej usługi.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)
- [Instrukcje: Tworzenie usług systemu Windows](how-to-create-windows-services.md)
