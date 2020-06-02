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
ms.openlocfilehash: 128ff4887601431f75981f13b51a11469e65d65c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290477"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Instrukcje: Wyodrębnianie dnia tygodnia z określonej daty
.NET Framework ułatwia określenie dnia tygodnia dla określonej daty i wyświetlanie zlokalizowanej nazwy dnia tygodnia dla konkretnej daty. Wartość wyliczana wskazująca dzień tygodnia odpowiadający określonej dacie jest dostępna z <xref:System.DateTime.DayOfWeek%2A> <xref:System.DateTimeOffset.DayOfWeek%2A> właściwości lub. Z kolei pobieranie nazwy dnia tygodnia jest operacją formatowania, którą można wykonać, wywołując metodę formatowania, taką jak metoda wartości daty i godziny `ToString` lub <xref:System.String.Format%2A?displayProperty=nameWithType> Metoda. W tym temacie przedstawiono sposób wykonywania tych operacji formatowania.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Aby wyodrębnić liczbę wskazującą dzień tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Użyj <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> właściwości lub, <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> Aby pobrać <xref:System.DayOfWeek> wartość wskazującą dzień tygodnia.  
  
3. W razie potrzeby CAST (w języku C#) lub Konwertuj (w Visual Basic) <xref:System.DayOfWeek> wartość na liczbę całkowitą.  
  
 Poniższy przykład wyświetla liczbę całkowitą reprezentującą dzień tygodnia dla określonej daty.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Aby wyodrębnić skróconą nazwę dnia tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Można wyodrębnić skróconą nazwę dnia tygodnia bieżącej kultury lub określonej kultury:  
  
    1. Aby wyodrębnić skróconą nazwę dnia tygodnia dla bieżącej kultury, wywołaj metodę wartości daty i godziny <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> wystąpienia, a następnie Przekaż ciąg "ddd" jako `format` parametr. Poniższy przykład ilustruje wywołanie <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Aby wyodrębnić skróconą nazwę dnia tygodnia dla określonej kultury, wywołaj wartość daty i godziny <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodę wystąpienia. Przekaż ciąg "ddd" jako `format` parametr. Przekaż albo <xref:System.Globalization.CultureInfo> <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje kulturę, której nazwa dnia tygodnia ma być pobierana jako `provider` parametr. Poniższy kod ilustruje wywołanie <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> metody przy użyciu <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę FR-fr.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Aby wyodrębnić pełną nazwę dnia tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Można wyodrębnić pełną nazwę dnia tygodnia bieżącej kultury lub określonej kultury:  
  
    1. Aby wyodrębnić nazwę dnia tygodnia dla bieżącej kultury, wywołaj metodę wartości daty i godziny <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> wystąpienia, a następnie Przekaż ciąg "dddd" jako `format` parametr. Poniższy przykład ilustruje wywołanie <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Aby wyodrębnić nazwę dnia tygodnia dla określonej kultury, wywołaj wartość daty i godziny <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodę wystąpienia. Przekaż ciąg "dddd" jako `format` parametr. Przekaż albo <xref:System.Globalization.CultureInfo> <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje kulturę, której nazwa dnia tygodnia ma być pobierana jako `provider` parametr. Poniższy kod ilustruje wywołanie <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> metody przy użyciu <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę ES-es.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Przykład  
 Przykład ilustruje wywołania <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> właściwości i i <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> metody, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> Aby pobrać liczbę reprezentującą dzień tygodnia, skróconą nazwę dnia tygodnia i pełną nazwę dnia tygodnia dla określonej daty.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Poszczególne języki mogą zapewniać funkcje, które duplikują lub uzupełniają funkcje udostępniane przez .NET Framework. Na przykład Visual Basic obejmuje dwie takie funkcje:  
  
- `Weekday`, która zwraca liczbę wskazującą dzień tygodnia określonej daty. Uważa wartość porządkową pierwszego dnia tygodnia, która ma być taka, natomiast Właściwość uważa, że jest <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> równa zero.  
  
- `WeekdayName`, która zwraca nazwę tygodnia w bieżącej kulturze, która odnosi się do określonego numeru dnia tygodnia.  
  
 Poniższy przykład ilustruje użycie Visual Basic `Weekday` i `WeekdayName` funkcji.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Można również użyć wartości zwracanej przez <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> Właściwość w celu pobrania nazwy dnia tygodnia z określonej daty. Wymaga to tylko wywołania <xref:System.Enum.ToString%2A> metody na <xref:System.DayOfWeek> wartości zwracanej przez właściwość. Jednak ta technika nie tworzy zlokalizowanej nazwy dnia tygodnia dla bieżącej kultury, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]

## <a name="see-also"></a>Zobacz także

- [Standardowe ciągi formatujące datę i godzinę](standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatujące datę i godzinę](custom-date-and-time-format-strings.md)
