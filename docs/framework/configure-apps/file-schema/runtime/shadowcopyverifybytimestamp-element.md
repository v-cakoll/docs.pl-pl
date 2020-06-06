---
title: <shadowCopyVerifyByTimestamp> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115727"
---
# <a name="shadowcopyverifybytimestamp-element"></a>\<shadowCopyVerifyByTimestamp> Element
Określa, czy kopiowanie w tle używa domyślnego zachowania uruchamiania wprowadzonego w .NET Framework 4, czy przywraca zachowanie uruchamiania wcześniejszych wersji .NET Framework.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|enabled|Atrybut wymagany.<br /><br /> Określa, czy domeny aplikacji używające kopiowania w tle porównują sygnatury czasowe zestawów podczas uruchamiania, aby określić, czy zestaw został zaktualizowany przed skopiowaniem zestawu w tle.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Podczas uruchamiania program kopiuje tylko te zestawy, które zostały zaktualizowane od czasu ostatniego skopiowania do katalogu kopii w tle. Jest to wartość domyślna dla .NET Framework 4.|  
|fałsz|Przywraca zachowanie uruchamiania poprzednich wersji .NET Framework, które było skopiowane wszystkie pliki podczas uruchamiania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od .NET Framework 4, zestawy są kopiowane w tle, tylko wtedy, gdy ich sygnatury czasowe wskazują, że zostały zmienione od czasu ostatniego skopiowania do katalogu kopii w tle. Skraca to czas uruchamiania dla wielu aplikacji używających kopiowania w tle, zgodnie z opisem w obszarze [kopiowania w tle](../../../app-domains/shadow-copy-assemblies.md). W przypadku aplikacji z wysoką wartością procentową i częstotliwością aktualizacji zestawu mogą nie być korzystne zmiany w zachowaniu. W takim przypadku można użyć tego elementu, aby przywrócić zachowanie poprzednich wersji .NET Framework.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć domyślne zachowanie podczas uruchamiania kopiowania w tle w .NET Framework 4 i przywrócić zachowanie uruchamiania poprzednich wersji .NET Framework.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Kopiowanie zestawów w tle](../../../app-domains/shadow-copy-assemblies.md)
