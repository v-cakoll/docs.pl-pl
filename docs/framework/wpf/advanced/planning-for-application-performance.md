---
title: Planowanie wydajności aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
ms.openlocfilehash: 3fadba2fe8036fc558e18f80bd7cb1ffc977b762
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632117"
---
# <a name="planning-for-application-performance"></a>Planowanie wydajności aplikacji
Powodzenie osiągnąć cele dotyczące wydajności zależy od tego, jak dobrze opracowywania strategii wydajności. Planowanie jest pierwszy etap w opracowywaniu każdego produktu. W tym temacie opisano kilka bardzo proste zasady opracowanie strategii dobrą wydajność.  
  
## <a name="think-in-terms-of-scenarios"></a>Myślą w kategoriach scenariuszy  
 Scenariusze pomogą Ci skupić się na krytycznych składników aplikacji. Scenariusze zazwyczaj są uzyskiwane z klienci także konkurencyjnych produktów. Zawsze zapoznają się z klientami i Dowiedz się, co naprawdę sprawia, że ich cieszymy produktu i produktów swojej konkurencji. Opinie klientów może pomóc ustalić podstawowy scenariusz aplikacji. Na przykład Jeśli projektujesz składnik, który będzie używany podczas uruchamiania jest prawdopodobne, że ten składnik zostanie wywołana tylko raz podczas uruchamiania aplikacji. Czas uruchamiania staje się klucza scenariusza. Inne przykłady scenariuszy klucza może mieć szybkość klatek żądanej sekwencji animacji lub maksymalną dozwoloną dla aplikacji zestaw roboczy.  
  
## <a name="define-goals"></a>Zdefiniuj cele  
 Cele pomocne podczas określania, czy aplikacja działa szybciej lub wolniej. Należy zdefiniować cele, dla wszystkich scenariuszy. Wszystkie cele dotyczące wydajności, które definiujesz powinna być oparta na oczekiwania Twoich klientów. Może być trudne do wydajności zestawu, których cykl cele na wczesnym etapie podczas tworzenia aplikacji, gdy nadal istnieje wiele nierozwiązane problemy. Jednak zaleca się Ustaw początkowe cel i przejrzeć go w późniejszej niż nie do celem jest w ogóle.  
  
## <a name="understand-your-platform"></a>Omówienie platformy  
 Obsługa zawsze cyklu pomiaru, badania, rafinacja/poprawianie w cyklu rozwoju aplikacji. Od początku do końca cyklu tworzenia oprogramowania, należy do pomiaru wydajności Twojej aplikacji w środowisku niezawodne, stabilna. Należy unikać zmienność spowodowany czynnikami zewnętrznymi. Na przykład podczas testowania wydajności, należy wyłączyć oprogramowanie antywirusowe lub żadnych aktualizacji automatycznych, takich jak wiadomości SMS, wyników testów w celu uniknięcia obniżenie wydajności. Po mają mierzona wydajność aplikacji, należy zidentyfikować zmiany, które będą powodować największych ulepszenia. Po zmodyfikowaniu aplikacji, uruchom ponownie tego cyklu.  
  
## <a name="make-performance-tuning-an-iterative-process"></a>Wprowadź proces iteracyjny dostrajania wydajności  
 Należy wiedzieć względny koszt każdej funkcji, które będą używane. Na przykład użycie odbicia w programie Microsoft .NET Framework jest zwykle wydajność intensywnego pod względem zasobów obliczeniowych, więc chcesz z niego korzystać rozsądnie. Nie oznacza to uniknąć użycia odbicia, tylko, że należy zachować ostrożność równoważyć wymagania dotyczące wydajności aplikacji z wymaganiami dotyczącymi wydajności funkcji, których używasz.  
  
## <a name="build-towards-graphical-richness"></a>Tworzenie kierunku bogactwa graficzne  
 Technika do tworzenia skalowalnych podejście do osiągnięcia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wydajność aplikacji jest utworzenie kierunku graficzny złożonością i złożoności. Zawsze uruchamiaj przy użyciu co najmniej intensywnie wykorzystujących zasoby wydajności do osiągnięcia celów scenariusza. Po użytkownik osiąganiu tych celów, tworzyć kierunku bogactwa graficzne, przy użyciu więcej wydajności intensywnie korzystających z funkcji zawsze pamiętając o cele scenariusza. Należy pamiętać, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest bardzo zaawansowaną platformę i zapewnia bardzo rozbudowane funkcje graficzne. Korzystanie z funkcji intensywnie korzystających z wydajnością bez zastanowienia może niekorzystnie wpłynąć na wydajność aplikacji ogólnej.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Formanty są założenia rozszerzalny poprzez umożliwienie rozprzestrzeniania się całej dostosowywanie ich wyglądu, podczas zmieniania nie ich zachowanie kontroli. Dzięki wykorzystaniu style, szablony danych i szablony kontrolek, możesz utworzyć i stopniowo rozwijać dostosowywany [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] który dostosowuje się do wymagań dotyczących wydajności.  
  
## <a name="see-also"></a>Zobacz także
- [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
- [Wykorzystanie możliwości sprzętu](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Zachowanie obiektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)
- [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
- [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Inne zalecenia dotyczące wydajności](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
