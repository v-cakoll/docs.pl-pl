---
title: Wykonywanie niezależnych od kultury zmian wielkości liter
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
ms.openlocfilehash: 7b2dee03619e24c5a2845699a06e88abab0c594b
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160134"
---
# <a name="performing-culture-insensitive-case-changes"></a>Wykonywanie niezależnych od kultury zmian wielkości liter
Metody <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>i <xref:System.Char.ToLower%2A?displayProperty=nameWithType> zapewniają przeciążenia, które nie akceptują żadnych parametrów. Domyślnie te przeciążenia bez parametrów wykonują zmiany wielkości liter na podstawie wartości <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. Powoduje to generowanie wyników z uwzględnieniem wielkości liter, które mogą się różnić w zależności od kultury. Aby określić, czy chcesz, aby zmiany wielkości liter były zależne od kultury lub niewrażliwe na kulturę, należy użyć przeciążenia tych metod, które wymagają jawnego określenia parametru `culture`. W przypadku zmian wielkości liter z uwzględnieniem kultury należy określić `CultureInfo.CurrentCulture` dla parametru `culture`. W przypadku zmian wielkości liter bez uwzględniania kultur Określ `CultureInfo.InvariantCulture` dla parametru `culture`.  
  
 Często ciągi są konwertowane do standardowej wielkości liter, aby ułatwić późniejsze wyszukiwanie. Gdy ciągi są używane w ten sposób, należy określić `CultureInfo.InvariantCulture` dla parametru `culture`, ponieważ wartość <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> może ulec zmianie między czasem zmiany wielkości liter i czasem przeszukiwania.  
  
 Jeśli decyzja dotycząca zabezpieczeń jest oparta na operacji zmiany wielkości liter, operacja powinna być niezależna od kultury, aby upewnić się, że wartość `CultureInfo.CurrentCulture`nie wpłynie na wynik. Zapoznaj się z sekcją "porównania ciągów, które wykorzystują bieżącą kulturę" w artykule [najlepsze rozwiązania dotyczące korzystania z ciągów](../../../docs/standard/base-types/best-practices-strings.md) , aby zapoznać się z przykładem, w jaki sposób operacje na ciągach zależnych od kultury mogą generować niespójne wyniki.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Korzystając z metod String.ToUpper i String.ToLower  
 W przypadku przejrzystości kodu zaleca się, aby zawsze używać przeciążeń `String.ToUpper` i `String.ToLower` metod, które umożliwiają jawne określenie parametru `culture`. Na przykład poniższy kod wykonuje wyszukiwanie identyfikatorów. Operacja `key.ToLower` domyślnie jest zależna od kultury, ale to zachowanie nie jest jasne w przypadku odczytywania kodu.  
  
### <a name="example"></a>Przykład  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 Jeśli chcesz, aby operacja `key.ToLower` była niezależna od kultury, należy zmienić poprzedni przykład w następujący sposób, aby jawnie użyć `CultureInfo.InvariantCulture` podczas zmieniania wielkości liter.  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>Korzystając z metod Char.ToUpper i Char.ToLower  
 Mimo że metody `Char.ToUpper` i `Char.ToLower` mają takie same charakterystyki jak metody `String.ToUpper` i `String.ToLower`, jedynymi kulturami, których dotyczy, są turecki (Turcja) i azerbejdżański (łaciński, Azerbejdżan). Są to jedyne dwie kultury, w których występują różnice dotyczące wielkości liter. Aby uzyskać więcej informacji o tym unikatowym mapowaniu przypadku, zobacz sekcję "wielkość liter" w temacie klasy <xref:System.String>. W przypadku przejrzystości kodu i zapewnienia spójnych wyników zaleca się, aby zawsze używać przeciążeń tych metod, które pozwalają jawnie określić parametr `culture`.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
