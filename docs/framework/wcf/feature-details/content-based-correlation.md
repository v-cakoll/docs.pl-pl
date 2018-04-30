---
title: Korelacja na podstawie zawartości
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f46a2b68-8d24-4122-bbee-9573fc3f9fb4
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b4ebd49fbed12f1e8120e67f32496cd782531da
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="content-based-correlation"></a>Korelacja na podstawie zawartości
Gdy usługi przepływu pracy komunikację z klientami oraz innymi usługami, często istnieje części danych w ramach wymiany wiadomości, które jednoznacznie odnosi się komunikat do konkretnego wystąpienia. Na podstawie zawartości korelacji używa tych danych w komunikacie, takich jak numer lub kolejności ID klienta do wyznaczania tras wiadomościom do wystąpienia przepływu pracy właściwe. W tym temacie opisano sposób korzystania na podstawie zawartości korelacji w przepływach pracy.  
  
## <a name="using-content-based-correlation"></a>Przy użyciu korelacji na podstawie zawartości  
 Korelacja na podstawie zawartości jest używany, gdy usługi przepływu pracy posiada wiele metod, które są udostępniane przez pojedynczego klienta i element danych w ramach wymiany wiadomości identyfikuje odpowiednie wystąpienie.  
  
> [!NOTE]
>  Na podstawie zawartości korelacji jest przydatne, gdy nie można użyć korelacji kontekstu, ponieważ powiązanie nie jest jednym z obsługiwanych kontekstu powiązania programu exchange. Aby uzyskać więcej informacji o kontekście korelacji, zobacz [wymiana kontekstu](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).  
  
 Każde działanie obsługi wiadomości, używane podczas komunikacji te należy określić lokalizację danych w komunikacie, który unikatowo identyfikuje wystąpienie. Jest to zrobić, podając <xref:System.ServiceModel.MessageQuerySet>, za pomocą <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> lub <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, który wysyła zapytanie do wiadomości dla element lub elementy danych, które jednoznacznie zidentyfikować wystąpienie.  
  
> [!WARNING]
>  Dane, które służy do identyfikacji wystąpienia jest wartość skrótu na klucz korelacji. Można uważać, aby upewnić się, że dane używane na potrzeby korelacji jest unikatowa w przeciwnym razie kolizji w formie skrótu klucza może wystąpić i komunikaty można rozsyłanymi. Na przykład korelacji wyłącznie na nazwy klienta może spowodować kolizji, ponieważ może być wielu klientów o takiej samej nazwie. Dwukropkiem (`:`) nie powinna być używana jako część danych używane do korelacji wiadomości, ponieważ jest już używany do ograniczania kluczy i wartości do utworzenia ciąg, który jest następnie mieszany kwerendy komunikatów.  
  
 W poniższym przykładzie początkowej <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> w usłudze przepływu pracy zwraca `OrderId`, które są następnie przekazywane przez klienta w wywołaniu następujące <xref:System.ServiceModel.Activities.Receive> aktywności w usłudze przepływu pracy.  
  
 [!code-csharp[CFX_ContentCorrelation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#1)]  
  
 W poprzednim przykładzie przedstawiono na podstawie zawartości korelacji, który został zainicjowany przez <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.MessageQuerySet> Określa, czy dane używane do identyfikowania kolejnych komunikatów do tej usługi jest `OrderId`.  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 <xref:System.ServiceModel.Activities.Receive> Działaniu występującym <xref:System.ServiceModel.Activities.SendReply> w przepływie pracy wykonuje korelacji, który został zainicjowany przez <xref:System.ServiceModel.Activities.SendReply>. Zarówno działania udostępnianie takie same <xref:System.ServiceModel.Activities.CorrelationHandle>, ale każda z nich ma własny <xref:System.ServiceModel.MessageQuerySet> i <xref:System.ServiceModel.XPathMessageQuery> określający, gdzie dane identyfikacyjne jest w szczególności wiadomości. W działaniu, które inicjuje korelację to <xref:System.ServiceModel.MessageQuerySet> została określona w <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> właściwości oraz wszystkie następujące <xref:System.ServiceModel.Activities.Receive> działań, zostanie określona, przy użyciu <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości.  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 Korelacja na podstawie zawartości mogą być inicjowane przez żadnego działania obsługi komunikatów (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.ReceiveReply>) podczas przepływu danych jako część komunikatu. Jeśli określonych danych nie przepływu jako część wiadomości, a następnie mogą być inicjowane w jawnie przy użyciu <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. Jeśli wielu fragmentów danych są wymagane do unikatowej identyfikacji wiadomości, a następnie można dodać wielu zapytań do <xref:System.ServiceModel.MessageQuerySet>. W tych przykładach <xref:System.ServiceModel.Activities.CorrelationHandle> podany wprost do każdej z tych czynności przy użyciu `CorrelatesWith` lub `CorrelationHandle` właściwości, ale jeśli istnieje tylko jedna korelacja wymagane dla całego przepływu pracy, takich jak w tym przykładzie gdzie wszystko są powiązane z na `OrderId`, zarządzanie dojścia korelacji niejawne zapewniane przez <xref:System.ServiceModel.Activities.WorkflowServiceHost> jest wystarczająca.  
  
## <a name="using-the-initializecorrelation-activity"></a>Za pomocą działania InitializeCorrelation  
 W poprzednim przykładzie `OrderId` skierowana do wywołującego za pośrednictwem <xref:System.ServiceModel.Activities.SendReply> działanie jest to gdzie korelację został zainicjowany. Takie samo zachowanie można zrobić za pomocą <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. <xref:System.ServiceModel.Activities.InitializeCorrelation> Działanie ma <xref:System.ServiceModel.Activities.CorrelationHandle> i słownika elementów, które reprezentują danych służy do mapowania komunikat na prawidłowe wystąpienie. Umożliwia <xref:System.ServiceModel.Activities.InitializeCorrelation> działania w poprzednim przykładzie usuń <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> z <xref:System.ServiceModel.Activities.SendReply> działania i zainicjować przy użyciu korelacji <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.  
  
 [!code-csharp[CFX_ContentCorrelation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#4)]  
  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> Działanie jest następnie używane w przepływie pracy, po zmiennych, które są przechowywane dane są wypełnione, lecz przed <xref:System.ServiceModel.Activities.Receive> działanie, które są powiązane z zainicjowane <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
 [!code-csharp[CFX_ContentCorrelation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#5)]  
  
## <a name="configuring-xpath-queries-using-the-workflow-designer"></a>Konfigurowanie kwerendy XPath za pomocą projektanta przepływów pracy  
 W poprzednich przykładach działania i zapytania XPath używane w zapytaniach wiadomości zostały określone w kodzie. Projektant przepływu pracy w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] również umożliwia generowanie wyrażenia XPath z `DataContract` typów dla korelacji na podstawie zawartości. Pierwsze wyrażenie XPath skonfigurowana w poprzednim przykładzie został skonfigurowany pod kątem <xref:System.ServiceModel.Activities.SendReply>.  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 Aby skonfigurować wyrażenie XPath dla działania obsługi wiadomości w Projektancie przepływów pracy, wybierz działanie w Projektancie przepływów pracy. Jeśli działanie inicjuje korelację, co w poprzednim przykładzie, kliknij przycisk wielokropka **CorrelationInitializers** właściwości w **właściwości** okna. Spowoduje to wyświetlenie **dodać inicjatorów korelacji** okno dialogowe. W tym oknie dialogowym można określić typ korelacji i wybrać zawartość, która jest używana do korelacji. <xref:System.ServiceModel.Activities.CorrelationHandle> Zmienna jest określona w **dodać inicjatora** wybrania pola oraz typ korelacji i dane używane na potrzeby korelacji z **kwerendy XPath** części okna dialogowego.  
  
 ![Okno dialogowe CorrelationInitializer](../../../../docs/framework/wcf/feature-details/media/correlationinitializerdlg.jpg "CorrelationInitializerDlg")  
  
 Drugiego zapytania XPath w poprzednim przykładzie został skonfigurowany w <xref:System.ServiceModel.Activities.Receive> działania.  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 Aby skonfigurować Kwerenda XPath dla działania obsługi komunikatów, które nie inicjuje korelację, wybierz działanie w Projektancie przepływów pracy, a następnie kliknij przycisk wielokropka, dla **CorrelatesOn** właściwości w  **Właściwości** okna. Spowoduje to wyświetlenie **definicji CorrelatesOn** okno dialogowe.  
  
 ![Definicja CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlatesondialog.jpg "CorrelatesOnDialog")  
  
 W tym oknie dialogowym Określ <xref:System.ServiceModel.Activities.CorrelationHandle> i wybierz elementy w **kwerendy XPath** listy w celu skonstruowania zapytania XPath.
