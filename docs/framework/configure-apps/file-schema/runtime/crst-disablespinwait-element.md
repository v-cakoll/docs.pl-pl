---
title: < element > Crst_DisableSpinWait
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 0683081183081e249b2a9c89e1a6a15f638fb339
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117637"
---
# <a name="crst_disablespinwait-element"></a>\<element > Crst_DisableSpinWait

Określa, czy należy wyłączyć funkcję "oczekiwanie" podczas oczekiwania na sekcję krytyczną.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<Crst_DisableSpinWait >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**dostępny**|Określa, czy oczekiwanie na przejście na sekcje krytyczne, gdy są one z nimi związane, jest wyłączone.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|1|Wyłączenie pokrętła — oczekiwanie, jeśli nie można uzyskać sekcji krytycznej.|  
|0|Nie należy wyłączać elementu "oczekiwanie", jeśli nie można uzyskać sekcji krytycznej. Jest to wartość domyślna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje o różnych ustawieniach konfiguracji środowiska uruchomieniowego.|  
  
## <a name="example"></a>Przykład  

W poniższym przykładzie jest wyłączone obracanie w sekcji o kluczowym znaczeniu.  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
