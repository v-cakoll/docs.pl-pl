---
title: <enforceFIPSPolicy> Element
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: 0d6dd291a24928487a040c0427f058dee80bf836
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117385"
---
# <a name="enforcefipspolicy-element"></a>\<enforceFIPSPolicy> Element
Określa, czy należy wymusić wymaganie konfiguracji komputera, że algorytmy kryptograficzne muszą być zgodne z FIPS (Federal Information Processing Standards).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|enabled|Atrybut wymagany.<br /><br /> Określa, czy należy włączyć wymuszanie wymagania konfiguracji komputera, że algorytmy kryptograficzne muszą być zgodne ze standardem FIPS.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`true`|Jeśli komputer jest skonfigurowany tak, aby wymagania algorytmów kryptograficznych były zgodne ze standardem FIPS, to wymaganie jest wymuszane. Jeśli klasa implementuje algorytm, który nie jest zgodny z FIPS, konstruktory lub `Create` metody dla tej klasy generują wyjątki, gdy są uruchamiane na tym komputerze. Domyślnie włączone.|  
|`false`|Algorytmy kryptograficzne używane przez aplikację nie są wymagane do zgodności ze standardem FIPS, niezależnie od konfiguracji komputera.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od .NET Framework 2,0, tworzenie klas implementujących algorytmy kryptograficzne jest kontrolowane przez konfigurację komputera. Jeśli komputer jest skonfigurowany tak, aby wymagał zgodności algorytmów z FIPS, a Klasa implementuje algorytm, który nie jest zgodny ze standardem FIPS, każda próba utworzenia wystąpienia tej klasy zgłasza wyjątek. Konstruktory zgłaszają <xref:System.InvalidOperationException> wyjątek, a metody zgłaszają `Create` <xref:System.Reflection.TargetInvocationException> wyjątek z <xref:System.InvalidOperationException> wyjątkiem wewnętrznym.  
  
 Jeśli aplikacja jest uruchamiana na komputerach, których konfiguracje wymagają zgodności ze standardem FIPS, a aplikacja używa algorytmu, który nie jest zgodny z FIPS, można użyć tego elementu w pliku konfiguracji, aby uniemożliwić środowisko uruchomieniowe języka wspólnego (CLR) Wymuszanie zgodności ze standardem FIPS. Ten element został wprowadzony w dodatku Service Pack 1 .NET Framework 2,0.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uniemożliwić środowisku CLR Wymuszanie zgodności ze standardem FIPS.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Model kryptografii](../../../../standard/security/cryptography-model.md)
