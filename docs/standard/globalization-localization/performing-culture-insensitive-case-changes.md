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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f560e3b080f6355d4e0c433c2a2218fbcbc6d72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="performing-culture-insensitive-case-changes"></a>Wykonywanie niezależnych od kultury zmian wielkości liter
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, I <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody udostępniają przeciążeń, które nie akceptują parametrów. Domyślnie te przeciążenia bez parametrów wykonują zmiany wielkości liter na podstawie wartości z <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. Daje to wyniki z uwzględnieniem wielkości liter, które zależą od kultury. Aby umożliwić Wyczyść, czy wielkość zmiany, które mają być zależne od kultury lub niezależnych od kultury, należy używać przeciążeń tych metod, które wymagają jawnie określić `culture` parametru. Zależne od kultury zmian wielkości liter, można określić `CultureInfo.CurrentCulture` dla `culture` parametru. Niezależne od kultury zmian wielkości liter, można określić `CultureInfo.InvariantCulture` dla `culture` parametru.  
  
 Często ciągi są konwertowane na standardowe wielkości liter, aby włączyć wyszukiwanie łatwiejsze później. W przypadku używania ciągów w ten sposób można określić `CultureInfo.InvariantCulture` dla `culture` parametru, ponieważ wartość <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> nie może zmienić od godziny, zmieniający wielkość liter podczas wyszukiwania.  
  
 Jeśli decyzja zabezpieczeń jest oparta na operację zmiany wielkości, operacja powinna być niezależne od kultury aby upewnić się, że wynik nie ma wpływu na wartość `CultureInfo.CurrentCulture`. Zobacz sekcję "Ciąg porównania który Użyj bieżącej kultury" [najlepsze rozwiązania dotyczące ciągów za pomocą](../../../docs/standard/base-types/best-practices-strings.md) artykułu, na przykład, który demonstruje sposób zależne od kultury operacje na ciągach może spowodować niespójne wyniki.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Korzystając z metod String.ToUpper i String.ToLower  
 Dla jasności kodu, zaleca się zawsze używaj przeciążeń `String.ToUpper` i `String.ToLower` metod, które umożliwiają określenie `culture` parametru jawnie. Na przykład następujący kod przeprowadza wyszukiwanie identyfikator. `key.ToLower` Operacja jest zależne od kultury domyślnej, ale to zachowanie nie jest jasne, na podstawie odczytu kodu.  
  
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
  
 Jeśli chcesz `key.ToLower` operacji, uzyskanie niezależnych od kultury, należy zmienić poprzednim przykładzie w następujący sposób, aby jawnie używać `CultureInfo.InvariantCulture` podczas zmiany w przypadku.  
  
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
 Mimo że `Char.ToUpper` i `Char.ToLower` metody mają te same parametry jako `String.ToUpper` i `String.ToLower` metody, tylko kultury, których dotyczy to turecki (Turcja) i Azerbejdżański (łaciński, Azerbejdżan). Są to tylko dwa kultur różnice jednoznakowym wielkości liter. Aby uzyskać więcej informacji na temat to unikatowy mapowanie przypadków, zobacz sekcję "Wielkości liter" w <xref:System.String> klasy tematu. Dla jasności kodu i zapewnić spójne wyniki, zaleca się zawsze używaj przeciążeń tych metod, które umożliwiają jawnie określić `culture` parametru.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
