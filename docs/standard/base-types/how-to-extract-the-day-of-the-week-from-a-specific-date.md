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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bd4066fe0a2d9f26505976c13ac80e03554e0aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575730"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Porady: wyodrębnianie dnia tygodnia z określonej daty
.NET Framework ułatwia ustalenie liczby porządkowej dzień tygodnia dla określonej daty i wyświetlić nazwę zlokalizowanej dzień tygodnia dla określonej daty. Wartość wyliczenia, która wskazuje dzień tygodnia odpowiadający określonej daty jest dostępna z <xref:System.DateTime.DayOfWeek%2A> lub <xref:System.DateTimeOffset.DayOfWeek%2A> właściwości. Z kolei pobierania nazwy dni tygodnia operacji formatowania, które mogą być wykonywane przez wywołanie metody formatowania, takie jak wartość daty i godziny jest `ToString` metody lub <xref:System.String.Format%2A?displayProperty=nameWithType> metody. W tym temacie przedstawiono sposób wykonywania tych operacji formatowania.  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Aby wyodrębnić liczbę określającą dzień tygodnia z określonej daty  
  
1.  Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2.  Użyj <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> właściwości do pobrania <xref:System.DayOfWeek> wartość, która wskazuje dzień tygodnia.  
  
3.  W razie potrzeby rzutowanie (C#) lub przekonwertować (w języku Visual Basic) <xref:System.DayOfWeek> wartość na liczbę całkowitą.  
  
 W poniższym przykładzie przedstawiono całkowitą reprezentującą dzień tygodnia z określonej daty.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Aby wyodrębnić nazwy skróconej dzień tygodnia z określonej daty  
  
1.  Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2.  Można wyodrębnić nazwy skróconej dzień tygodnia bieżącej kultury lub kultury określonej:  
  
    1.  Aby wyodrębnić nazwy skróconej dzień tygodnia dla bieżącej kultury, należy wywołać wartość daty i godziny <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody wystąpienia i przekazać ciąg "ddd" jako `format` parametru. Poniższy przykład przedstawia wywołanie <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2.  Aby wyodrębnić nazwy skróconej dzień tygodnia dla określonej kultury, należy wywołać wartość daty i godziny <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody wystąpienia. Przekazać ciąg "ddd" jako `format` parametru. Przekaż albo <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje kultury, których chcesz pobrać jako nazwa dnia tygodnia `provider` parametru. Poniższy kod ilustruje wywołanie <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> przy użyciu metody <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje fr-FR kultury.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Aby wyodrębnić Pełna nazwa dnia tygodnia z określonej daty  
  
1.  Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.  
  
2.  Pełna nazwa dnia tygodnia bieżącej kultury lub określoną kulturę można wyodrębnić:  
  
    1.  Aby wyodrębnić nazwy dni tygodnia dla bieżącej kultury, należy wywołać wartość daty i godziny <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody wystąpienia i przekazać ciąg "dddd" jako `format` parametru. Poniższy przykład przedstawia wywołanie <xref:System.DateTime.ToString%28System.String%29> metody.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2.  Aby wyodrębnić nazwy dni tygodnia dla określonej kultury, należy wywołać wartość daty i godziny <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody wystąpienia. Przekazać ciąg "dddd" jako `format` parametru. Przekaż albo <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.DateTimeFormatInfo> obiekt, który reprezentuje kultury, których chcesz pobrać jako nazwa dnia tygodnia `provider` parametru. Poniższy kod ilustruje wywołanie <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> przy użyciu metody <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje es-ES kultury.  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a>Przykład  
 Wywołania pokazano w przykładzie <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> właściwości i <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> metody, aby pobrać liczbę reprezentującą dzień tygodnia, nazwy skróconej dzień tygodnia i Pełna nazwa dnia tygodnia dla określonej daty.  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 Poszczególne języki mogą zapewnić funkcje, których duplikatów lub uzupełniają funkcje udostępniane przez [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Na przykład Visual Basic zawiera dwie funkcje:  
  
-   `Weekday`, która zwraca liczbę wskazującą dzień tygodnia z określonej daty. Traktuje wartość porządkową pierwszego dnia tygodnia jedną, podczas gdy <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> właściwości uzna zero.  
  
-   `WeekdayName`, które zwraca nazwę tygodnia w bieżącej kultury, która odpowiada numerowi określonego dnia tygodnia.  
  
 Poniższy przykład przedstawia użycie Visual Basic `Weekday` i `WeekdayName` funkcji.  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 Umożliwia także wartość zwrócona przez <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> właściwości pobrać nazwy dni tygodnia z określonej daty. Wymaga to tylko wywołania <xref:System.Enum.ToString%2A> metoda <xref:System.DayOfWeek> wartość zwracana przez właściwość. Ta technika nie tworzy jednak nazwę zlokalizowanej dzień tygodnia dla bieżącej kultury, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
