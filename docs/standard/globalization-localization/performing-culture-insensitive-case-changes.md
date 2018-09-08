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
ms.openlocfilehash: 844b0edb93b93704c4886495c673dc0496f7ba71
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192980"
---
# <a name="performing-culture-insensitive-case-changes"></a>Wykonywanie niezależnych od kultury zmian wielkości liter
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, I <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metod, zapewnienia przeciążenia, które nie akceptują parametrów. Domyślnie te przeciążenia bez parametrów wykonywania przypadków zmienia się zależnie od wartości <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. To daje wyniki uwzględniana wielkość liter, które mogą się różnić od kultury. Aby umożliwić jednoznacznie wskazuje, czy chcesz, aby zmiany wielkości liter kultury lub niewrażliwość na ustawienia kulturowe, należy używać przeciążenia tych metod, które wymagają jawnie określić `culture` parametru. Zależne od kultury zmian wielkości liter, określ `CultureInfo.CurrentCulture` dla `culture` parametru. W przypadku niezależnych od kultury zmian wielkości liter, określić `CultureInfo.InvariantCulture` dla `culture` parametru.  
  
 Często ciągi są konwertowane na standardowym przypadku można włączyć później ułatwić wyszukiwanie. Jeśli ciągi są używane w ten sposób, należy określić `CultureInfo.InvariantCulture` dla `culture` parametru, ponieważ wartość <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> potencjalnie może się zmieniać między zostanie zmieniony tak czas i czas, który występuje wyszukiwania.  
  
 Jeśli decyzja dot. zabezpieczeń opiera się na operację zmiany sprawy, operacja nie powinna zależeć od kultury upewnij się, że wynik nie wpływa wartość `CultureInfo.CurrentCulture`. Zobacz sekcję "Ciągów porównań, użyj bieżącej kultury" [najlepsze rozwiązania dotyczące Using Strings](../../../docs/standard/base-types/best-practices-strings.md) artykuł dla przykładu, który demonstruje sposób zależne od kultury operacje na ciągach mogą generować niespójne wyniki.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Korzystając z metod String.ToUpper i String.ToLower  
 Czystości kodu zaleca się używanie przeciążenia `String.ToUpper` i `String.ToLower` metod, które pozwalają na określenie `culture` parametru jawnie. Na przykład poniższy kod przeprowadza wyszukiwanie identyfikatora. `key.ToLower` Operacja jest zależne od kultury domyślnej, ale to zachowanie nie jest jasne, z kodu.  
  
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
  
 Jeśli chcesz `key.ToLower` operację, aby być uwzględniana kultura, należy zmienić poprzedni przykład, w następujący sposób, aby jawnie użyć `CultureInfo.InvariantCulture` podczas zmiany sprawy.  
  
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
 Mimo że `Char.ToUpper` i `Char.ToLower` metody mają takie same charakterystyki jak `String.ToUpper` i `String.ToLower` metod, tylko kultur, które wpływają na to, turecki (Turcja) i Azerbejdżański (łaciński, Azerbejdżan). Są to tylko dwie kultury z różnicami wielkość liter w wyrazie pojedynczych znaków. Aby uzyskać więcej informacji na temat to unikatowy mapowanie przypadków, zobacz sekcję "Wielkość liter w wyrazie" w <xref:System.String> temat poświęcony klasie. Czystości kodu i zapewnić spójne wyniki, zaleca się zawsze używaj przeciążenia tych metod, które pozwalają na określenie jawnie `culture` parametru.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
