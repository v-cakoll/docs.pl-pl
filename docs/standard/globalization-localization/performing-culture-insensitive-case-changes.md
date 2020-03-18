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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160134"
---
# <a name="performing-culture-insensitive-case-changes"></a>Wykonywanie niezależnych od kultury zmian wielkości liter
, <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>i <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody zapewniają przeciążenia, które nie akceptują żadnych parametrów. Domyślnie te przeciążenia bez parametrów wykonują zmiany przypadków <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>na podstawie wartości . Daje to wyniki z uwzględnieniem wielkości liter, które mogą się różnić w zależności od kultury. Aby było jasne, czy zmiany wielkości liter mają być zależne od kultury lub kultury niewrażliwe, należy użyć przeciążenia tych metod, które wymagają jawnie określić `culture` parametr. W przypadku zmian wielkości `CultureInfo.CurrentCulture` liter `culture` uwzględniających kulturę określ parametr. W przypadku zmian wielkości liter `CultureInfo.InvariantCulture` nieuwzględniających kulturę określ parametr. `culture`  
  
 Często ciągi są konwertowane na standardowy przypadek, aby umożliwić łatwiejsze późniejsze odszukanie. Gdy ciągi są używane w ten `CultureInfo.InvariantCulture` sposób, należy określić dla parametru, `culture` ponieważ wartość <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> może ulec zmianie między czasem, że sprawa jest zmieniana i czas, w którym występuje odciąganie.  
  
 Jeśli decyzja o zabezpieczeniach jest oparta na operacji zmiany przypadku, operacja powinna być niewrażliwa `CultureInfo.CurrentCulture`na kulturę, aby upewnić się, że wartość wyniku nie ma wpływu na wynik . Zobacz "Porównania ciągów, które używają bieżącej kultury" sekcji [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md) artykułu na przykład, który pokazuje, jak operacje ciągów zależnych od kultury może powodować niespójne wyniki.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Korzystając z metod String.ToUpper i String.ToLower  
 Dla jasności kodu zaleca się, aby zawsze używać `String.ToUpper` `String.ToLower` przeciążenia i metody, `culture` które umożliwiają jawnie określić parametr. Na przykład poniższy kod wykonuje wyszukiwania identyfikatora. Operacja `key.ToLower` jest domyślnie zależne od kultury, ale to zachowanie nie jest jasne z czytania kodu.  
  
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
  
 Jeśli `key.ToLower` chcesz, aby operacja była niewrażliwa na kulturę, należy zmienić poprzedni `CultureInfo.InvariantCulture` przykład w następujący sposób, aby jawnie użyć podczas zmiany sprawy.  
  
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
 Chociaż `Char.ToUpper` i `Char.ToLower` metody mają takie same `String.ToUpper` cechy `String.ToLower` jak i metody, jedynymi kulturami, których to dotyczy, są tureckie (Turcja) i Azerbejdżan (łaciński, Azerbejdżan). Są to jedyne dwie kultury z jednopostaciowymi różnicami w obudowie. Aby uzyskać więcej informacji na temat tego unikatowego <xref:System.String> mapowania wielkości liter, zobacz sekcję "Obudowa" w temacie klasy. Dla jasności kodu i zapewnienia spójnych wyników zaleca się, aby zawsze używać przeciążenia tych `culture` metod, które umożliwiają jawnie określić parametr.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
