---
title: "Planowanie wydajności aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6bdb140d90de02fa817c55a05f40e57fcd0d636c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="planning-for-application-performance"></a>Planowanie wydajności aplikacji
Powodzenie osiągnięcia cele wydajności zależy od tego, jak również opracowanie strategii wydajności. Planowanie to pierwszy etap w tworzeniu każdego produktu. W tym temacie opisano kilka bardzo proste zasady opracowanie strategii dobrą wydajność.  
  
## <a name="think-in-terms-of-scenarios"></a>Wziąć pod uwagę w scenariuszach  
 Scenariusze mogą pomóc skupić się na krytycznych składników aplikacji. Scenariusze są zazwyczaj uzyskiwane z klientów, jak również konkurencyjnych. Zawsze bada klientów i dowiedzieć się, co naprawdę sprawia, że ich radością o produktu i produktach konkurencji. Opinie klientów może pomóc ustalić scenariusz głównej aplikacji. Na przykład w przypadku projektowania składnika, który będzie używany podczas uruchamiania, jest prawdopodobne, że składnik zostanie wywołana tylko raz, podczas uruchamiania aplikacji. Czas uruchamiania staje się danego scenariusza klucza. Inne przykłady scenariuszy klucza może być szybkość klatek żądaną sekwencji animacji lub maksymalna dozwolona dla aplikacji zestawu roboczego.  
  
## <a name="define-goals"></a>Zdefiniuj cele  
 Cele pomóc ustalić, czy aplikacja działa szybciej lub wolniej. Należy zdefiniować cele dla wszystkich scenariuszy. Wszystkie cele dotyczące wydajności zdefiniowanych przez użytkownika powinny być oparte na oczekiwań klientów. Może być trudne wydajności zestawu cele na wczesnym etapie w projektowanie aplikacji cyklu są nadal wiele nierozwiązane problemy. Jednak zaleca się ustawić cel początkowej i popraw go później niż do ma na celu na wszystkich.  
  
## <a name="understand-your-platform"></a>Zrozumienie platformy  
 Obsługa zawsze cyklu pomiaru, badanie, uściślenie/korygowanie cyklu rozwoju aplikacji. Od początku do końca cyklu programowanie należy do pomiaru wydajności aplikacji w środowisku niezawodnych, stabilna. Należy unikać zmienności spowodowany czynnikami zewnętrznymi. Na przykład podczas testowania wydajności, należy Wyłącz oprogramowanie antywirusowe, lub żadnych aktualizacji automatycznych, takich jak SMS, wyniki testów kolejność, która nie ma wpływu na wydajność. Po ma mierzona wydajności aplikacji, należy zidentyfikować zmiany, które poprawia największych. Po zmodyfikowaniu aplikacji, należy uruchomić ponownie cyklu.  
  
## <a name="make-performance-tuning-an-iterative-process"></a>Wprowadź procesem iteracyjnym dostrajania wydajności  
 Należy poznać względny koszt każdej funkcji, które będą używane. Na przykład użyj odbicia w [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] jest zazwyczaj wydajności znacznym pod względem zasoby przetwarzania danych, więc czy ma być rozważnie. Oznacza to, uniknąć użycia odbicia, tylko, że należy zachować ostrożność równoważyć wymagania dotyczące wydajności aplikacji z wymaganiami dotyczącymi wydajności, funkcji, których używasz.  
  
## <a name="build-towards-graphical-richness"></a>Tworzenie kierunku siłę graficznego  
 Technika klucza do tworzenia skalowalnych podejście do osiągnięcia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wydajność aplikacji jest utworzenie kierunku siłę graficznego i złożoności. Zawsze rozpoczynać przy użyciu co najmniej wydajności zasobów znacznym celach scenariusza. Po osiągnięcie tych celów, kompilacji kierunku siłę graficzny dzięki funkcjom więcej wydajności znacznym, zawsze pamiętając o cele scenariusza. Należy pamiętać, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest bardzo zaawansowaną platformę i zapewnia bardzo zaawansowane funkcje graficzne. Przy użyciu funkcji znacznym wydajności bez planowania może niekorzystnie wpłynąć na wydajność aplikacji ogólnej.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Formanty są z założenia rozszerzony w celu umożliwienia dostosowania rozpowszechniania całej ich wyglądu, podczas nie zmieniając ich zachowanie kontroli. Dzięki wykorzystaniu style, szablony danych i szablonów kontrolki, możesz utworzyć i przyrostowo rozwijać, można dostosowywać [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] która dostosowuje się do wymagań dotyczących wydajności.  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Wykorzystanie możliwości sprzętu](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Zachowanie obiektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Inne zalecenia dotyczące wydajności](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
