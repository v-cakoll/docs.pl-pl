---
title: <UseRandomizedStringHashAlgorithm> Element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153780"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedStringHashAlgorithm> Element
Określa, czy środowisko uruchomieniowe języka wspólnego oblicza kody skrótów dla ciągów na podstawie poszczególnych domen aplikacji.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy kody skrótów dla ciągów są obliczane na podstawie poszczególnych domen aplikacji.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`0`|Środowisko uruchomieniowe języka wspólnego nie oblicza kodów skrótów dla ciągów na podstawie poszczególnych domen aplikacji; pojedynczy algorytm służy do obliczania kodów skrótów ciągów. Domyślnie włączone.|  
|`1`|Środowisko uruchomieniowe języka wspólnego oblicza kody skrótów dla ciągów na podstawie poszczególnych domen aplikacji. Identyczne ciągi w różnych domenach aplikacji i w różnych procesach będą mieć różne kody skrótów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.StringComparer> Klasa i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> Metoda używają jednego algorytmu wyznaczania wartości skrótu, który tworzy spójny kod skrótu w różnych domenach aplikacji. Jest to równoznaczne z ustawieniem `enabled` atrybutu `<UseRandomizedStringHashAlgorithm>` elementu na `0` . Jest to algorytm wyznaczania wartości skrótu używany w .NET Framework 4.  
  
 <xref:System.StringComparer>Klasa i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> Metoda mogą również używać innego algorytmu wyznaczania wartości skrótu, który oblicza kody skrótów dla poszczególnych domen aplikacji. W związku z tym kody skrótów dla równoważnych ciągów różnią się w różnych domenach aplikacji. Jest to funkcja opcjonalna. Aby skorzystać z niego, należy ustawić `enabled` atrybut `<UseRandomizedStringHashAlgorithm>` elementu na `1` .  
  
 Wyszukiwanie ciągu w tabeli skrótów jest zazwyczaj operacją O (1). Jednak w przypadku wystąpienia dużej liczby kolizji wyszukiwanie może być operacją O (n<sup>2</sup>). Można użyć `<UseRandomizedStringHashAlgorithm>` elementu konfiguracji, aby wygenerować losowy algorytm wyznaczania wartości skrótu na domenę aplikacji, co z kolei ogranicza liczbę potencjalnych kolizji, szczególnie gdy klucze, z których są obliczane kody skrótów, są oparte na danych wejściowych użytkowników.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `DisplayString` klasę, która zawiera znak prywatny w postaci ciągu, `s` którego wartością jest "to jest ciąg". Zawiera również `ShowStringHashCode` metodę, która wyświetla wartość ciągu i jego kod skrótu wraz z nazwą domeny aplikacji, w której jest wykonywana metoda.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 W przypadku uruchomienia tego przykładu bez podawania pliku konfiguracji wyświetlane są dane wyjściowe podobne do poniższych. Należy zauważyć, że kody skrótów dla ciągu są identyczne w obu domenach aplikacji.  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Jeśli jednak dodasz następujący plik konfiguracji do katalogu przykładu, a następnie uruchomisz przykład, kody skrótów dla tego samego ciągu różnią się w zależności od domeny aplikacji.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Gdy plik konfiguracji jest obecny, w przykładzie są wyświetlane następujące dane wyjściowe:  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
