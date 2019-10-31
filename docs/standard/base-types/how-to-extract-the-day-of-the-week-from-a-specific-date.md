---
title: 'Porady: wyodrębnianie dnia tygodnia z określonej daty'
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
ms.openlocfilehash: 771bd0276310eecb534fb80836faadb1a8aa10bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084202"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Porady: wyodrębnianie dnia tygodnia z określonej daty
.NET Framework ułatwia określenie dnia tygodnia dla określonej daty i wyświetlanie zlokalizowanej nazwy dnia tygodnia dla konkretnej daty. Wartość wyliczana wskazująca dzień tygodnia odpowiadający określonej dacie jest dostępna z właściwości <xref:System.DateTime.DayOfWeek%2A> lub <xref:System.DateTimeOffset.DayOfWeek%2A>. Z kolei pobieranie nazwy dnia tygodnia jest operacją formatowania, którą można wykonać, wywołując metodę formatowania, taką jak Metoda `ToString` daty i godziny lub metoda <xref:System.String.Format%2A?displayProperty=nameWithType>. W tym temacie przedstawiono sposób wykonywania tych operacji formatowania.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Aby wyodrębnić liczbę wskazującą dzień tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Użyj właściwości <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType>, aby pobrać <xref:System.DayOfWeek> wartość wskazującą dzień tygodnia.  
  
3. W razie potrzeby CAST (in C#) lub Convert (w Visual Basic) wartość <xref:System.DayOfWeek> na liczbę całkowitą.  
  
 Poniższy przykład wyświetla liczbę całkowitą reprezentującą dzień tygodnia dla określonej daty.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Aby wyodrębnić skróconą nazwę dnia tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Można wyodrębnić skróconą nazwę dnia tygodnia bieżącej kultury lub określonej kultury:  
  
    1. Aby wyodrębnić skróconą nazwę dnia tygodnia dla bieżącej kultury, wywołaj wartość daty i godziny <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> lub metodę wystąpienia <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> i przekaż ciąg "ddd" jako parametr `format`. Poniższy przykład ilustruje wywołanie metody <xref:System.DateTime.ToString%28System.String%29>.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Aby wyodrębnić skróconą nazwę dnia tygodnia dla określonej kultury, wywołaj wartość daty i godziny <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lub metodę wystąpienia <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>. Przekaż ciąg "ddd" jako parametr `format`. Przekaż <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje kulturę, której nazwa dnia tygodnia ma być pobierana jako parametr `provider`. Poniższy kod ilustruje wywołanie metody <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> przy użyciu obiektu <xref:System.Globalization.CultureInfo>, który reprezentuje kulturę fr-FR.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Aby wyodrębnić pełną nazwę dnia tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Można wyodrębnić pełną nazwę dnia tygodnia bieżącej kultury lub określonej kultury:  
  
    1. Aby wyodrębnić nazwę dnia tygodnia dla bieżącej kultury, wywołaj metodę <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> wystąpienia wartości daty i godziny, a następnie Przekaż ciąg "dddd" jako parametr `format`. Poniższy przykład ilustruje wywołanie metody <xref:System.DateTime.ToString%28System.String%29>.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Aby wyodrębnić nazwę dnia tygodnia dla określonej kultury, wywołaj wartość daty i godziny <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lub metodę wystąpienia <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>. Przekaż ciąg "dddd" jako parametr `format`. Przekaż <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje kulturę, której nazwa dnia tygodnia ma być pobierana jako parametr `provider`. Poniższy kod ilustruje wywołanie metody <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> przy użyciu obiektu <xref:System.Globalization.CultureInfo>, który reprezentuje kulturę es-ES.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Przykład  
 Przykład ilustruje wywołania właściwości <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> oraz metody <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType>, aby pobrać liczbę reprezentującą dzień tygodnia, skróconą nazwę dnia tygodnia i pełną nazwę dnia tygodnia dla określonej daty.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Poszczególne języki mogą zapewniać funkcje, które duplikują lub uzupełniają funkcje udostępniane przez .NET Framework. Na przykład Visual Basic obejmuje dwie takie funkcje:  
  
- `Weekday`, która zwraca liczbę wskazującą dzień tygodnia określonej daty. Uważa wartość porządkową pierwszego dnia tygodnia, która ma być taka, natomiast Właściwość <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> uważa, że jest równa zero.  
  
- `WeekdayName`, która zwraca nazwę tygodnia w bieżącej kulturze, która odnosi się do określonego numeru dnia tygodnia.  
  
 Poniższy przykład ilustruje użycie `Weekday` Visual Basic i funkcji `WeekdayName`.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Możesz również użyć wartości zwróconej przez właściwość <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType>, aby pobrać nazwę dnia tygodnia z określonej daty. Wymaga to tylko wywołania metody <xref:System.Enum.ToString%2A> na wartości <xref:System.DayOfWeek> zwróconej przez właściwość. Jednak ta technika nie tworzy zlokalizowanej nazwy dnia tygodnia dla bieżącej kultury, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
