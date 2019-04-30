---
title: <ThrowUnobservedTaskExceptions>, element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdce2181490d32212cd2629e98267e43bbe0d334
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674002"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions> Element
Określa, czy zadanie nieobsługiwanych wyjątków powinien wygasają uruchomionego procesu.  
  
 \<Konfiguracja >  
\<runtime>  
\<ThrowUnobservedTaskExceptions>  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy zadanie nieobsługiwanych wyjątków powinien wygasają uruchomionego procesu.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie kończy proces uruchomiony nieobsłużony wyjątek zadania. Domyślnie włączone.|  
|`true`|Kończy proces uruchomiony nieobsłużony wyjątek zadania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
|||  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wyjątek, który jest skojarzony z <xref:System.Threading.Tasks.Task> nie zostało spełnione, istnieje nie <xref:System.Threading.Tasks.Task.Wait%2A> operacji, element nadrzędny nie jest podłączony i <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> właściwości nie została ona odczytana wyjątek zadania jest uważany za niewidocznego.  
  
 W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], domyślnie, jeśli <xref:System.Threading.Tasks.Task> ma niewidocznego wyjątek bezużyteczne, finalizator zgłasza wyjątek i kończy proces. Przed zakończeniem procesu jest określany przez chronometrażu wyrzucania elementów bezużytecznych i finalizacji jest zakończona.  
  
 Aby ułatwić programistom pisanie kodu asynchronicznego, na podstawie zadań, [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] zmienia to zachowanie domyślne niewidocznego wyjątków. Niezauważalne wyjątki, które nadal powodują <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> zdarzenia, ale domyślnie nie zakończyć proces. Zamiast tego wyjątek jest ignorowany, po wywołaniu zdarzenia, niezależnie od tego, czy program obsługi zdarzeń przestrzega wyjątku.  
  
 W [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], możesz użyć [ \<throwunobservedtaskexceptions — > element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) w pliku konfiguracyjnym aplikacji, aby umożliwić [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] zachowanie zostanie zgłoszony wyjątek.  
  
 Można również określić zachowanie wyjątek w jednym z następujących sposobów:  
  
- Przez ustawienie zmiennej środowiskowej `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
- Przez ustawienie rejestru DWORD wartości throwunobservedtaskexceptions — = 1 w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Klucz NETFramework.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak włączyć zgłaszanie wyjątków w zadaniach przy użyciu pliku konfiguracji aplikacji.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak niewidocznego wyjątku z zadania. Kod musi działać jako wydana program działał prawidłowo.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
