---
title: element < Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f89f0558c11e229fef2ca3cd619e3c033f12c858
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754676"
---
# <a name="crstdisablespinwait-element"></a>\<Crst_DisableSpinWait > element

Określa, czy wyłączyć pokrętła — oczekiwanie na sekcję krytyczną rywalizacją.  
  
 \<Konfiguracja >  
\<runtime>  
\<Crst_DisableSpinWait >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Włączone**|Określa, czy pokrętła — oczekiwanie na sekcje krytyczne, gdy są one rywalizacją jest wyłączona.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|1|Wyłącz pokrętła oczekiwania, gdy nie można pobrać sekcję krytyczną.|  
|0|Nie należy wyłączać pokrętła oczekiwania, gdy sekcję krytyczną, nie można pobrać. Jest to wartość domyślna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje o różnych ustawień konfiguracji środowiska uruchomieniowego.|  
  
## <a name="example"></a>Przykład  

Poniższy przykład wyłącza pokrętła waiting, w sekcji krytycznych, gdy z rywalizacją.  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
