---
title: mc:Ignorable — Atrybut
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: d8fdeec8784c9a44c9b272a0a5a8b9c56ace5230
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458817"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable — Atrybut
Określa, które [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] prefiksy przestrzeni nazw napotkane w pliku znaczników mogą zostać zignorowane przez procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Atrybut `mc:Ignorable` obsługuje zgodność znaczników zarówno dla niestandardowego mapowania przestrzeni nazw, jak i dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wersji.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>Użycie atrybutu języka XAML (pojedynczy prefiks)  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>Użycie atrybutu języka XAML (dwa prefiksy)  
  
```xaml  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*ignorablePrefix, ignorablePrefix1 itd.*|Dowolny prawidłowy ciąg prefiksu na specyfikację XML 1,0.|  
|*ignorableUri*|Dowolny prawidłowy identyfikator URI służący do wyznaczania przestrzeni nazw, zgodnie ze specyfikacją XML 1,0.|  
|*ThisElementCanBeIgnored*|Element, który może być ignorowany przez implementacje procesora [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], jeśli nie można rozpoznać typu podstawowego.|  
  
## <a name="remarks"></a>Uwagi  
 Prefiks przestrzeni nazw [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] `mc` jest zalecaną konwencją prefiksu do użycia podczas mapowania `http://schemas.openxmlformats.org/markup-compatibility/2006`przestrzeni nazw zgodności [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Elementy lub atrybuty, w których części prefiksu nazwy elementu są identyfikowane jako `mc:Ignorable` nie będą powodować błędów podczas przetwarzania przez procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Jeśli ten atrybut nie może zostać rozpoznany jako typ podstawowy lub konstrukcja programistyczna, ten element jest ignorowany. Należy jednak zauważyć, że zignorowane elementy nadal mogą generować dodatkowe błędy analizy dla dodatkowych wymagań elementu, które są efektami ubocznymi tego elementu, który nie jest przetwarzany. Na przykład model zawartości określonego elementu może wymagać dokładnie jednego elementu podrzędnego, ale jeśli określony element podrzędny znajdował się w prefiksie `mc:Ignorable`, a określony element podrzędny nie mógł zostać rozpoznany jako typ, wówczas procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] może zgłosić błąd.  
  
 `mc:Ignorable` stosuje się tylko do mapowań przestrzeni nazw do ciągów identyfikatorów. `mc:Ignorable` nie ma zastosowania do mapowań przestrzeni nazw na zestawy, które określają przestrzeń nazw CLR i zestaw (lub domyślny bieżący plik wykonywalny jako zestaw).  
  
 W przypadku wdrażania procesora [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacja procesora nie może podnieść lub przetwarzać błędów podczas rozpoznawania typów dla każdego elementu lub atrybutu, który jest kwalifikowany przez prefiks identyfikowany jako `mc:Ignorable`. Ale implementacja procesora może nadal zgłaszać wyjątki, które są pomocniczym wynikiem elementu, którego nie można załadować lub przetworzyć, np. przykładem elementu z pojedynczym elementem podrzędnym.  
  
 Domyślnie procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zignoruje zawartość w ignorowanym elemencie. Można jednak określić dodatkowy atrybut, [MC: ProcessContent Attribute](mc-processcontent-attribute.md), aby wymagać ciągłego przetwarzania zawartości w zignorowanym elemencie przez następny dostępny element nadrzędny.  
  
 W atrybucie można określić wiele prefiksów, używając co najmniej jednego znaku odstępu jako separatora, na przykład: `mc:Ignorable="ignore1 ignore2"`.  

 Przestrzeń nazw `http://schemas.openxmlformats.org/markup-compatibility/2006` definiuje inne elementy i atrybuty, które nie są udokumentowane w tym obszarze zestawu SDK. Aby uzyskać więcej informacji, zobacz [Specyfikacja zgodności znaczników XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze, atrybut](presentationoptions-freeze-attribute.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Dokumenty w WPF](documents-in-wpf.md)
