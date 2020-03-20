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
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153818"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedZamykacień> element
Określa, czy nieobsługiwalne wyjątki zadań powinny zakończyć uruchomiony proces.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedZadkustawy>**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy nieobsługiwalne wyjątki zadań powinny zakończyć uruchomiony proces.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie kończy uruchomionego procesu dla nieobsługiwał wyjątku zadania. Domyślnie włączone.|  
|`true`|Kończy uruchomiony proces dla nieobsługiwał wyjątku zadania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
|||  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wyjątek, który jest <xref:System.Threading.Tasks.Task> skojarzony z a <xref:System.Threading.Tasks.Task.Wait%2A> nie została zaobserwowana, nie ma <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> operacji, nadrzędny nie jest dołączony, a właściwość nie została odczytana wyjątek zadania jest uważany za niezaobserwowany.  
  
 W .NET Framework 4, domyślnie, <xref:System.Threading.Tasks.Task> jeśli, który ma niezaobserwowany wyjątek jest zbierane śmieci, finalizatora zgłasza wyjątek i kończy proces. Zakończenie procesu zależy od czasu wyrzucania elementów bezużytecznych i finalizacji.  
  
 Aby ułatwić deweloperom pisanie kodu asynchronicznego na podstawie zadań, program .NET Framework 4.5 zmienia to domyślne zachowanie dla niezaobserwowanych wyjątków. Niezaobserwowane wyjątki nadal powodują, że <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> zdarzenie ma zostać zwodowane, ale domyślnie proces nie kończy się. Zamiast tego wyjątek jest ignorowany po zdarzenia jest wywoływana, niezależnie od tego, czy program obsługi zdarzeń przestrzega wyjątku.  
  
 W .NET Framework 4.5 można użyć [ \<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) w pliku konfiguracji aplikacji, aby włączyć zachowanie .NET Framework 4 zgłaszania wyjątku.  
  
 Zachowanie wyjątku można również określić w jeden z następujących sposobów:  
  
- Ustawiając zmienną `COMPlus_ThrowUnobservedTaskExceptions` `set COMPlus_ThrowUnobservedTaskExceptions=1`środowiskową ( ).  
  
- Ustawiając wartość rejestru DWORD ThrowUnobservedTaskExceptions = 1 w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak włączyć zgłaszanie wyjątków w zadaniach przy użyciu pliku konfiguracji aplikacji.  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak nieobserwowany wyjątek jest generowany z zadania. Kod musi być uruchomiony jako zwolniony program, aby działał poprawnie.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
