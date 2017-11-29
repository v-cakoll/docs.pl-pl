---
title: "&lt;Throwunobservedtaskexceptions —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d171c2058a79476d99c5952cc6a697f126af81c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a>&lt;Throwunobservedtaskexceptions —&gt; — Element
Określa, czy zadanie nieobsługiwanych wyjątków powinny przerwanie uruchomiony proces.  
  
 \<Konfiguracja >  
\<Runtime >  
\<Throwunobservedtaskexceptions — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy zadanie nieobsługiwanych wyjątków powinny przerwanie uruchomiony proces.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie kończy proces uruchomione zadania nieobsługiwany wyjątek. Domyślnie włączone.|  
|`true`|Kończy proces uruchomione zadania nieobsługiwany wyjątek.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
|||  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wyjątek, który jest skojarzony z <xref:System.Threading.Tasks.Task> nie zostało spełnione, brak nie <xref:System.Threading.Tasks.Task.Wait%2A> operacji, element nadrzędny nie jest dołączony i <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> właściwości nie została przeczytana zadania wyjątek jest uznawany za niezaobserwowany.  
  
 W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], przez domyślne, jeśli <xref:System.Threading.Tasks.Task> mający niezaobserwowany wyjątek bezużytecznych, finalizator zgłasza wyjątek i kończy proces. Zakończenie procesu jest określana przez czas wyrzucanie elementów bezużytecznych i finalizacji.  
  
 Aby ułatwić deweloperom pisanie kodu asynchroniczny oparty na zadaniach, [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] zmieni to domyślne zachowanie dla wyznaczonego wyjątków. Być niezauważalna wyjątki nadal powodują <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> się zdarzenia, ale domyślnie nie zakończyć proces. Zamiast tego wyjątku została zignorowana po wywołaniu zdarzenia, niezależnie od tego, czy program obsługi zdarzeń przestrzega wyjątek.  
  
 W [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], można użyć [ \<throwunobservedtaskexceptions — > element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) w pliku konfiguracji aplikacji, aby włączyć [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] zachowanie Zgłaszanie wyjątku.  
  
 Można również określić zachowanie wyjątek w jednym z następujących sposobów:  
  
-   Przez ustawienie zmiennej środowiskowej `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
-   Przez ustawienie rejestru DWORD wartość throwunobservedtaskexceptions — = 1 w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Klucz NETFramework.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można włączyć zgłaszanie wyjątków w zadania przy użyciu pliku konfiguracji aplikacji.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak niezaobserwowany wyjątek zadania. Kod musi być uruchamiany jako wydanych program działał prawidłowo.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
