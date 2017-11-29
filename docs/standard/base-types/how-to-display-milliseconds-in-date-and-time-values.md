---
title: "Porady: wyświetlanie ilości milisekund wartości daty i godziny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 260d202eb0a218a6657bc719e36da6f39138e54e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a>Porady: wyświetlanie ilości milisekund wartości daty i godziny
Domyślne metody formatowania daty i czasu, takie jak <xref:System.DateTime.ToString?displayProperty=nameWithType>, zawierają godziny, minuty i sekundy wartości czasu, ale wykluczają składnik milisekund. W tym temacie pokazano jak dołączyć datę i składnik czasu w milisekundach w sformatowanym ciągu daty i czasu.  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a>Aby wyświetlić składnik milisekund wartości DateTime  
  
1.  Jeśli pracujesz z ciągiem znaków reprezentującym datę, należy przekonwertować ciąg do wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> przy użyciu statycznej metody <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType>.  
  
2.  W celu wyodrębnienia ciągu reprezentującego składnik czasu w milisekundach, należy wywołać wartość daty i godziny metody <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> lub <xref:System.DateTimeOffset.ToString%2A> i przekazać wzorzec w niestandardowym formacie `fff` lub `FFF`, oddzielnie lub z innym niestandardowym specyfikatorem formatu, jak parametr `format`.  
  
## <a name="example"></a>Przykład  
 W przykładzie wyświetlono składnik wartości milisekund <xref:System.DateTime> i <xref:System.DateTimeOffset> w konsoli, zarówno samodzielnie, jak i uwzględniając dłuższy ciąg daty i czasu.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 Wzorzec formatu `fff` zawiera dowolne zera końcowe w wartościach milisekund. Wzorzec formatu `FFF` pomija je. Różnice tę ilustruje poniższy przykład.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 Problemem przy definiowaniu kompletnego niestandardowego specyfikatora formatu, który zawiera składnik milisekund daty i czasu, jest to ze definiuje on format zakodowany, który może nie odpowiadać na rozmieszczenie elementów czasu bieżącej kultury w aplikacji. Lepszą alternatywą jest pobranie jednej daty i czasu wyświetlającej wzorzec określony przez obiekt bieżącej kultury <xref:System.Globalization.DateTimeFormatInfo> i zmodyfikować go, aby uwzględniał milisekundy. Ten przykład ilustruje takie podejście. Pobierany jest wzorzec pełnej daty i czasu dla bieżącej kultury z właściwości <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType>, a następnie niestandardowy wzorzec `.ffff` jest wstawiany za wzorcem dla sekund. Należy zauważyć, że w przykładzie użyto wyrażenia regularnego do wykonania tej operacji w pojedynczym wywołaniu metody.  
  
 Aby wyświetlić część ułamkową sekund innych niż milisekund można określić specyfikator formatu niestandardowego. Na przykład niestandardowy specyfikator formatu `f` lub `F` wyświetla część dziesiętną sekund, niestandardowy specyfikator formatu `ff` lub `FF` wyświetla setną część sekund, natomiast niestandardowy specyfikator formatu `ffff` lub `FFFF` wyświetla część tysięczną sekund. Części ułamkowe milisekund są obcinane w zwracanym ciągu zamiast zaokrąglane. W poniższym przykładzie są używane następujące specyfikatory formatu.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  Istnieje możliwość wyświetlania bardzo małych części ułamkowych sekund, takie jak tysięczne sekund lub sto tysięczne sekund. Jednak te wartości mogą być nieistotne. Dokładność wartości daty i godziny zależy od rozdzielczości zegara systemu. W systemach operacyjnych Windows NT 3.5 (i późniejszych) oraz [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], rozdzielczość zegara wynosi około 10-15 milisekund.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skompiluj kod w wierszu polecenia za pomocą csc.exe lub vb.exe. Aby skompilować kod w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], należy umieścić go w szablonie projektu aplikacji konsolowej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [Niestandardowa data i godzina ciągi formatujące](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
