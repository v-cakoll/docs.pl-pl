---
title: <UseRandomizedStringHashAlgorithm>, element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153780"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedStringHashAlgorithm> Element
Określa, czy środowisko uruchomieniowe języka wspólnego oblicza kody mieszania dla ciągów na podstawie domeny aplikacji.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy kody skrótów dla ciągów są obliczane dla domeny dla aplikacji.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`0`|Środowisko wykonawcze języka wspólnego nie oblicza kodów skrótów dla ciągów na podstawie domeny aplikacji; pojedynczy algorytm jest używany do obliczania kodów skrótów ciągów. Domyślnie włączone.|  
|`1`|Środowisko wykonawcze języka wspólnego oblicza kody mieszania dla ciągów na podstawie domeny aplikacji. Identyczne ciągi w różnych domenach aplikacji i w różnych procesach będą miały różne kody skrótów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.StringComparer> klasa i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda używają algorytmu mieszania pojedynczego, który tworzy spójny kod mieszania w domenach aplikacji. Jest to równoważne `enabled` ustawieniu `<UseRandomizedStringHashAlgorithm>` atrybutu `0`elementu na . Jest to algorytm mieszania używany w .NET Framework 4.  
  
 Klasa <xref:System.StringComparer> i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda można również użyć innego algorytmu mieszania, który oblicza kody mieszania na podstawie domeny aplikacji. W rezultacie kody mieszania dla równoważnych ciągów będą się różnić w domenach aplikacji. Jest to funkcja opt-in; aby z niego skorzystać, należy `enabled` ustawić atrybut `<UseRandomizedStringHashAlgorithm>` elementu `1`na .  
  
 Wyszukiwanie ciągów w tabeli mieszania jest zazwyczaj operacją O(1). Jednak gdy wystąpi duża liczba kolizji, wyszukiwanie może stać się operacją O(n<sup>2).</sup> Za pomocą `<UseRandomizedStringHashAlgorithm>` elementu konfiguracji można wygenerować algorytm mieszania losowego dla domeny aplikacji, co z kolei ogranicza liczbę potencjalnych kolizji, szczególnie gdy klucze, z których są obliczane kody skrótów, są oparte na danych wprowadzanych przez użytkowników.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje `DisplayString` klasę, która zawiera `s`stałą prywatnego ciągu, której wartość jest "To jest ciąg". Zawiera również `ShowStringHashCode` metodę, która wyświetla wartość ciągu i jego kod skrótu wraz z nazwą domeny aplikacji, w której metoda jest wykonywana.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Po uruchomieniu przykład bez podaniu pliku konfiguracji, wyświetla dane wyjściowe podobne do następujących. Należy zauważyć, że kody skrótów dla ciągu są identyczne w dwóch domenach aplikacji.  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Jeśli jednak dodasz następujący plik konfiguracyjny do katalogu przykładu, a następnie uruchomisz przykład, kody skrótów dla tego samego ciągu będą się różnić w zależności od domeny aplikacji.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Gdy plik konfiguracyjny jest obecny, w przykładzie są wyświetlane następujące dane wyjściowe:  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
