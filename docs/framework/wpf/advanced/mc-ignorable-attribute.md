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
ms.openlocfilehash: a72b2886c63a80a4887aa16fc6a952fa837a800f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991445"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable — Atrybut
Określa, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] które prefiksy przestrzeni nazw napotkane w pliku znaczników mogą zostać zignorowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przez procesor. Ten `mc:Ignorable` atrybut obsługuje zgodność znaczników zarówno dla niestandardowego mapowania przestrzeni nazw, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jak i do przechowywania wersji.  
  
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
|*ThisElementCanBeIgnored*|Element, który może być ignorowany [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przez implementacje procesora, jeśli nie można rozpoznać typu podstawowego.|  
  
## <a name="remarks"></a>Uwagi  
 Prefiks przestrzeni nazw jest zalecaną konwencją prefiksu używaną podczas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mapowania przestrzeni `http://schemas.openxmlformats.org/markup-compatibility/2006`nazw zgodności. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] `mc`  
  
 Elementy lub atrybuty, w których część prefiksu nazwy elementu jest identyfikowana `mc:Ignorable` jako nie powoduje błędów podczas przetwarzania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przez procesor. Jeśli ten atrybut nie może zostać rozpoznany jako typ podstawowy lub konstrukcja programistyczna, ten element jest ignorowany. Należy jednak zauważyć, że zignorowane elementy nadal mogą generować dodatkowe błędy analizy dla dodatkowych wymagań elementu, które są efektami ubocznymi tego elementu, który nie jest przetwarzany. Na przykład model zawartości określonego elementu może wymagać dokładnie jednego elementu podrzędnego, ale jeśli określony element podrzędny znajduje się w `mc:Ignorable` prefiksie, a określony element podrzędny nie został rozpoznany jako typ, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor może Zgłoś błąd.  
  
 `mc:Ignorable`stosuje się tylko do mapowań przestrzeni nazw do ciągów identyfikatorów. `mc:Ignorable`nie dotyczy mapowań przestrzeni nazw do zestawów, które określają przestrzeń nazw CLR i zestaw (lub domyślny bieżący plik wykonywalny jako zestaw).  
  
 W przypadku wdrażania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora implementacja procesora nie może podnieść lub przetwarzać błędów podczas rozpoznawania typów dla każdego elementu lub atrybutu, który jest kwalifikowany przez prefiks identyfikowany jako `mc:Ignorable`. Ale implementacja procesora może nadal zgłaszać wyjątki, które są pomocniczym wynikiem elementu, którego nie można załadować lub przetworzyć, np. przykładem elementu z pojedynczym elementem podrzędnym.  
  
 Domyślnie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor zignoruje zawartość w ignorowanym elemencie. Można jednak określić dodatkowy atrybut, [MC: ProcessContent Attribute](mc-processcontent-attribute.md), aby wymagać ciągłego przetwarzania zawartości w zignorowanym elemencie przez następny dostępny element nadrzędny.  
  
 W atrybucie można określić wiele prefiksów, używając co najmniej jednego znaku odstępu jako separatora, na przykład: `mc:Ignorable="ignore1 ignore2"`.  

 `http://schemas.openxmlformats.org/markup-compatibility/2006` Przestrzeń nazw definiuje inne elementy i atrybuty, które nie są udokumentowane w tym obszarze zestawu SDK. Aby uzyskać więcej informacji, zobacz [Specyfikacja zgodności znaczników XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze, atrybut](presentationoptions-freeze-attribute.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Dokumenty w WPF](documents-in-wpf.md)
