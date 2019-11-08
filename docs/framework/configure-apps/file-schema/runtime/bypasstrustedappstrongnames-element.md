---
title: <bypassTrustedAppStrongNames> Element
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739085"
---
# <a name="bypasstrustedappstrongnames-element"></a>\<element > bypassTrustedAppStrongNames

Określa, czy pomijać weryfikację silnych nazw w zestawach pełnego zaufania, które są ładowane do <xref:System.AppDomain>pełnego zaufania.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<bypassTrustedAppStrongNames >**

## <a name="syntax"></a>Składnia

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy Funkcja pomijania, która pozwala uniknąć weryfikowania silnych nazw dla zestawów pełnego zaufania jest włączona. Gdy ta funkcja jest włączona, silne nazwy nie są sprawdzane pod kątem poprawności podczas ładowania zestawu. Wartość domyślna to `true`.|

## <a name="enabled-attribute"></a>Atrybut włączony

|Wartość|Opis|
|-----------|-----------------|
|`true`|Sygnatury o silnej nazwie w zestawach pełnego zaufania nie są sprawdzane, gdy zestawy są ładowane do <xref:System.AppDomain>pełnego zaufania. Domyślnie włączone.|
|`false`|Sygnatury silnej nazwy w zestawach pełnego zaufania są weryfikowane podczas ładowania zestawów do <xref:System.AppDomain>pełnego zaufania. Sygnatura o silnej nazwie jest sprawdzana tylko w celu poprawienia podpisu; nie jest porównywana z inną silną nazwą dla dopasowania.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Funkcja pomijania silnej nazwy pozwala uniknąć narzutu na weryfikację podpisów o silnej nazwie w przypadku zestawów o pełnym zaufaniu.

Funkcja Bypass ma zastosowanie do każdego zestawu, który jest podpisany silną nazwą i ma następującą charakterystykę:

- W pełni zaufane bez <xref:System.Security.Policy.StrongName> dowodów (na przykład ma `MyComputer`e dowody strefy).

- Załadowano do w pełni zaufanego <xref:System.AppDomain>.

- Załadowano z lokalizacji pod właściwością <xref:System.AppDomainSetup.ApplicationBase%2A> tej <xref:System.AppDomain>.

- Nie jest podpisany z opóźnieniem.

> [!NOTE]
> Jeśli funkcja pomijania została wyłączona dla wszystkich aplikacji na komputerze przy użyciu klucza rejestru, to ustawienie tego pliku konfiguracji nie ma żadnego wpływu. Aby uzyskać więcej informacji, zobacz [jak: wyłączanie funkcji pomijania silnej nazwy](../../../../standard/assembly/disable-strong-name-bypass-feature.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak określić zachowanie, które sprawdza podpis silnej nazwy w zestawach pełnego zaufania.

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Instrukcje: wyłączanie funkcji pomijania silnej nazwy](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
