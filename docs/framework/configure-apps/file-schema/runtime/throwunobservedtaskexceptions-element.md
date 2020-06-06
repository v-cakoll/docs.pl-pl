---
title: <ThrowUnobservedTaskExceptions> Element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153818"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions> Element
Określa, czy Nieobsłużone wyjątki zadań powinny kończyć uruchomiony proces.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy Nieobsłużone wyjątki zadań powinny kończyć uruchomiony proces.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie przerywa uruchomionego procesu dla nieobsłużonego wyjątku zadania. Domyślnie włączone.|  
|`true`|Kończy uruchomiony proces dla nieobsłużonego wyjątku zadania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
|||  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie zaobserwowano wyjątku, który jest skojarzony z programem, nie ma <xref:System.Threading.Tasks.Task> żadnej <xref:System.Threading.Tasks.Task.Wait%2A> operacji, element nadrzędny nie jest dołączony i <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> Właściwość nie została odczytana, ponieważ wyjątek zadania jest traktowany jako nieobserwowany.  
  
 W .NET Framework 4 domyślnie, jeśli dla, <xref:System.Threading.Tasks.Task> który ma niezauważalny wyjątek jest odzyskiwany, finalizator zgłasza wyjątek i kończy proces. Zakończenie procesu zależy od chronometrażu wyrzucania elementów bezużytecznych i finalizacji.  
  
 Aby ułatwić deweloperom pisanie kodu asynchronicznego na podstawie zadań, .NET Framework 4,5 zmienia to zachowanie domyślne dla nieobserwowanych wyjątków. Niezauważalne wyjątki nadal powodują <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> , że zdarzenie zostanie wywołane, ale domyślnie proces nie zostanie zakończony. Zamiast tego wyjątek jest ignorowany po wywołaniu zdarzenia, niezależnie od tego, czy program obsługi zdarzeń obserwuje wyjątek.  
  
 W .NET Framework 4,5 można użyć [ \<ThrowUnobservedTaskExceptions> elementu](throwunobservedtaskexceptions-element.md) w pliku konfiguracyjnym aplikacji, aby włączyć .NET Framework 4 zachowanie zgłaszania wyjątku.  
  
 Możesz również określić zachowanie wyjątku w jeden z następujących sposobów:  
  
- Ustawiając zmienną środowiskową `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ).  
  
- Ustawiając wartość DWORD rejestru ThrowUnobservedTaskExceptions = 1 w HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . Klucz NETFramework.  
  
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
 Poniższy przykład demonstruje, jak wyjątek niezauważalny jest generowany z zadania. Aby program działał prawidłowo, kod musi być uruchomiony.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
