---
title: 'Instrukcje: Wyodrębnianie dnia tygodnia z określonej daty'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- DateTime.DayOfWeek property
- DateTime.ToString method
- dates [.NET Framework], retrieving week information
- DateTimeOffset.DayOfWeek property
- dates [.NET Framework], day of week
- Weekday function
- day of week [.NET Framework]
- extracting day of week
- weekday names
- WeekdayName function
- numbers [.NET Framework], day of week
- formatting [.NET Framework], time
- DateTimeOffset.ToString method
- full weekday names
ms.assetid: 1c9bef76-5634-46cf-b91c-9b9eb72091d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c665cb590a090c546d50f780477c254344914a2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61861078"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Instrukcje: Wyodrębnianie dnia tygodnia z określonej daty
.NET Framework ułatwia ustalenie porządkowe dzień tygodnia dla określonej daty i wyświetlić nazwę zlokalizowanej dzień tygodnia dla określonej daty. Wartość wyliczana, który wskazuje dzień tygodnia odpowiadający określonej daty jest dostępne z <xref:System.DateTime.DayOfWeek%2A> lub <xref:System.DateTimeOffset.DayOfWeek%2A> właściwości. Pobieranie nazwy dnia tygodnia jest operacją formatowania, które mogą być wykonywane przez wywołanie metody formatowania, takie jak wartości daty i godziny `ToString` metody lub <xref:System.String.Format%2A?displayProperty=nameWithType> metody. W tym temacie przedstawiono sposób wykonywania tych operacji formatowania.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Aby wyodrębnić liczbę określającą dzień tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Użyj <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> właściwość służąca do pobierania <xref:System.DayOfWeek> wartość, która wskazuje dzień tygodnia.  
  
3. W razie potrzeby rzutowania (w języku C#) lub przekonwertować (w języku Visual Basic) <xref:System.DayOfWeek> wartości na liczbę całkowitą.  
  
 Poniższy przykład Wyświetla całkowitą reprezentującą dzień tygodnia z określonej daty.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Aby wyodrębnić nazwy dnia tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Można wyodrębnić nazwy dnia tygodnia bieżącej kultury lub określonej kultury:  
  
    1. Aby wyodrębnić nazwy dnia tygodnia bieżącej kultury, należy wywołać wartość daty i godziny <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodę wystąpienia, a następnie przekazać ten ciąg "ddd" jako `format` parametru. W poniższym przykładzie pokazano wywołanie metody <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Aby wyodrębnić nazwy dnia tygodnia dla określonej kultury, należy wywołać wartość daty i godziny <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodę wystąpienia. Przekaż ciąg "ddd" jako `format` parametru. Przekazać parametr <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje kulturę, której nazwa dnia tygodnia do pobrania jako `provider` parametru. Poniższy kod ilustruje wywołanie <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> przy użyciu metody <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje kultury fr-FR.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Aby wyodrębnić Pełna nazwa dnia tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Można wyodrębnić Pełna nazwa dnia tygodnia bieżącej kultury lub określonej kultury:  
  
    1. Aby wyodrębnić nazwy dnia tygodnia bieżącej kultury, należy wywołać wartość daty i godziny <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodę wystąpienia, a następnie przekazać ten ciąg "dddd" jako `format` parametru. W poniższym przykładzie pokazano wywołanie metody <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Aby wyodrębnić nazwy dnia tygodnia dla określonej kultury, należy wywołać wartość daty i godziny <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodę wystąpienia. Przekaż ciąg "dddd" jako `format` parametru. Przekazać parametr <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje kulturę, której nazwa dnia tygodnia do pobrania jako `provider` parametru. Poniższy kod ilustruje wywołanie <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> przy użyciu metody <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę, es-ES.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Przykład  
 W przykładzie pokazano wywołania <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> właściwości i <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> metody, aby pobrać liczbę reprezentującą dzień tygodnia, nazwy dnia tygodnia i Pełna nazwa dnia tygodnia dla określonej daty.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Poszczególne języki oferują funkcje, która duplikuje lub uzupełniają funkcje udostępniane przez [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Na przykład Visual Basic obejmuje dwa takie funkcje:  
  
- `Weekday`, która zwraca numer, który wskazuje dzień tygodnia z określonej daty. Traktuje wartości porządkowej pierwszy dzień tygodnia, aby być jednym z nich, podczas gdy <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> właściwość traktuje wynosić zero.  
  
- `WeekdayName`, która zwraca nazwę tygodnia w bieżącej kultury, która odpowiada numerowi danego dnia tygodnia.  
  
 Poniższy przykład ilustruje użycie języka Visual Basic `Weekday` i `WeekdayName` funkcji.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Umożliwia także wartość zwrócona przez obiekt <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> właściwość służąca do pobierania nazwy dnia tygodnia z określonej daty. Wymaga to jedynie po wywołaniu <xref:System.Enum.ToString%2A> metody <xref:System.DayOfWeek> wartość zwracana przez właściwość. Jednak ta technika nie generuje nazwę zlokalizowanej dzień tygodnia dla bieżącej kultury tak jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
