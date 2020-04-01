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
ms.openlocfilehash: 8eed7c0176a2c1f4beb472dff981d52e522c7e36
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523829"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Instrukcje: Wyodrębnianie dnia tygodnia z określonej daty
.NET Framework ułatwia określenie porządkowego dnia tygodnia dla określonej daty i wyświetlanie zlokalizowanej nazwy dnia tygodnia dla określonej daty. Wyliczona wartość, która wskazuje dzień tygodnia odpowiadający określonej dacie, jest dostępna z <xref:System.DateTime.DayOfWeek%2A> właściwości lub. <xref:System.DateTimeOffset.DayOfWeek%2A> Natomiast pobieranie nazwy dnia tygodnia jest operacją formatowania, którą można wykonać, wywołując metodę formatowania, `ToString` taką jak <xref:System.String.Format%2A?displayProperty=nameWithType> metoda wartości daty i godziny lub metoda. W tym temacie pokazano, jak wykonać te operacje formatowania.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Aby wyodrębnić liczbę wskazującą dzień tygodnia od określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Użyj <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> właściwość, <xref:System.DayOfWeek> aby pobrać wartość, która wskazuje dzień tygodnia.  
  
3. W razie potrzeby rzutuj (w języku C#) lub konwertuj <xref:System.DayOfWeek> (w języku Visual Basic) wartość na liczbę całkowitą.  
  
 W poniższym przykładzie jest wyświetlana liczba całkowita reprezentująca dzień tygodnia określonej daty.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Aby wyodrębnić skróconą nazwę dnia tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Można wyodrębnić skróconą nazwę dnia tygodnia bieżącej kultury lub określonej kultury:  
  
    1. Aby wyodrębnić skróconą nazwę dnia tygodnia dla bieżącej kultury, wywołaj wartość daty i godziny <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodę `format` wystąpienia i przekaż ciąg "ddd" jako parametr. Poniższy przykład ilustruje <xref:System.DateTime.ToString%28System.String%29> wywołanie metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. Aby wyodrębnić skróconą nazwę dnia tygodnia dla określonej kultury, należy <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> wywołać wartość daty i godziny lub metodę wystąpienia. Przekaż ciąg "ddd" `format` jako parametr. Przekaż <xref:System.Globalization.CultureInfo> obiekt lub <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje kulturę, której nazwa dnia `provider` tygodnia chcesz pobrać jako parametr. Poniższy kod ilustruje <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> wywołanie <xref:System.Globalization.CultureInfo> metody przy użyciu obiektu, który reprezentuje kulturę fr-FR.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Aby wyodrębnić pełną nazwę dnia tygodnia z określonej daty  
  
1. Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2. Można wyodrębnić pełną nazwę dnia tygodnia bieżącej kultury lub określonej kultury:  
  
    1. Aby wyodrębnić nazwę dnia tygodnia dla bieżącej kultury, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> wywołaj datę i godzinę wartości lub <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody wystąpienia `format` i przekazać ciąg "dddd" jako parametr. Poniższy przykład ilustruje <xref:System.DateTime.ToString%28System.String%29> wywołanie metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. Aby wyodrębnić nazwę dnia tygodnia dla określonej kultury, <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> należy <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> wywołać wartość daty i godziny lub metodę wystąpienia. Przekaż ciąg "dddd" `format` jako parametr. Przekaż <xref:System.Globalization.CultureInfo> obiekt lub <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje kulturę, której nazwa dnia `provider` tygodnia chcesz pobrać jako parametr. Poniższy kod ilustruje <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> wywołanie <xref:System.Globalization.CultureInfo> metody przy użyciu obiektu, który reprezentuje kultury es-ES.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Przykład  
 Przykład <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> ilustruje wywołania <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> właściwości i <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> i metody, aby pobrać numer, który reprezentuje dzień tygodnia, skróconą nazwę dnia tygodnia i pełną nazwę dnia tygodnia dla określonej daty.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Poszczególne języki mogą zapewniać funkcje, które powiela lub uzupełnia funkcje udostępniane przez program .NET Framework. Na przykład visual basic zawiera dwie takie funkcje:  
  
- `Weekday`, która zwraca liczbę wskazującą dzień tygodnia określonej daty. Uważa wartość porządkową pierwszego dnia tygodnia za jedną, podczas gdy <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> właściwość uważa ją za zerową.  
  
- `WeekdayName`, który zwraca nazwę tygodnia w bieżącej kulturze, która odpowiada określonemu numerowi dnia tygodnia.  
  
 Poniższy przykład ilustruje użycie `Weekday` języka `WeekdayName` Visual Basic i funkcji.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Można również użyć wartości zwróconej <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> przez właściwość, aby pobrać nazwę dnia tygodnia określonej daty. Wymaga to tylko wywołania <xref:System.Enum.ToString%2A> metody <xref:System.DayOfWeek> na wartość zwróconą przez właściwość. Jednak ta technika nie tworzy zlokalizowane nazwa dni tygodnia dla bieżącej kultury, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]

## <a name="see-also"></a>Zobacz też

- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
