---
title: "Właściwości zależności tylko do odczytu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31e4080416d5eb4fdfe5c33ec2b65e1dced6d012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="read-only-dependency-properties"></a>Właściwości zależności tylko do odczytu
W tym temacie opisano właściwości zależności tylko do odczytu, włącznie z istniejącej właściwości tylko do odczytu zależności i scenariusze i techniki tworzenia właściwości niestandardowych zależności tylko do odczytu.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz podstawowe scenariusze wdrażania właściwości zależności i jak metadanych są stosowane do właściwości niestandardowych zależności. Zobacz [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) i [metadanych właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) dla kontekstu.  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Istniejącej właściwości tylko do odczytu zależności  
 Niektóre właściwości zależności zdefiniowane w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] framework są tylko do odczytu. Typowe przyczyny służący do określania właściwości tylko do odczytu zależności jest, że są one właściwości, która powinna być używana do określenia stanu, ale których wpływ na tym stanie przez wiele czynników, ale tylko ustawienie właściwości w dany stan nie jest pożądana z Perspektywa projektu interfejsu użytkownika. Na przykład właściwość <xref:System.Windows.UIElement.IsMouseOver%2A> jest naprawdę tylko udostępniając stanu zgodnie z myszy danych wejściowych. Każda próba ta wartość programowo przez obejście wejście myszy wartość true, będzie nieprzewidywalny i mogłoby spowodować niespójność.  
  
 Z brakiem można ustawić, właściwości tylko do odczytu zależności nie są odpowiednie dla wielu scenariuszy, dla których zależności właściwości oferują zwykle rozwiązania (to znaczy: wiązanie bezpośrednio stylable wartość, sprawdzanie poprawności, animacji, dziedziczenia danych). Mimo iż nie można ustawić, tylko do odczytu zależności właściwości nadal mieć niektóre dodatkowe funkcje obsługiwane przez właściwości zależności w systemie właściwości. Najważniejsze możliwości pozostałych jest, że właściwość tylko do odczytu zależności nadal może być używana jako właściwość Wyzwalacze w stylu. Nie można włączyć wyzwalacze zwykłym [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości; musi on być właściwością zależności. Wyżej wymienionych <xref:System.Windows.UIElement.IsMouseOver%2A> właściwość jest idealne przykładowy scenariusz, w którym może być bardzo przydatne do definiowania stylów formantu, gdy niektóre właściwości visible, np. tło, pierwszego planu lub podobne właściwości połączone elementy wewnątrz kontroli ulegnie zmianie, gdy użytkownik umieszcza myszy nad niektórych zdefiniowanych region formantu. Zmiany właściwości tylko do odczytu zależności można także wykryte i zgłoszony przez system właściwości związanego z używaniem unieważniania procesów i to w rzeczywistości obsługuje funkcje wyzwalacza właściwości wewnętrznie.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Tworzenie niestandardowych zależności tylko do odczytu właściwości  
 Upewnij się zapoznać się z sekcją powyżej dotyczące Dlaczego właściwości tylko do odczytu zależności nie będzie działać w różnych scenariuszach typowe właściwości zależności. Ale jeśli jest to odpowiedni scenariusz, możesz utworzyć własną właściwość dependency tylko do odczytu.  
  
 Większa część procesu tworzenia właściwości zależności tylko do odczytu jest taki sam, jak opisano w [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) i [implementuje właściwości zależności](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) tematów. Istnieją trzy istotnych różnic:  
  
-   Podczas rejestrowania programu właściwości, należy wywołać <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> metody zamiast normalnych <xref:System.Windows.DependencyProperty.Register%2A> metoda rejestracji właściwości.  
  
-   Podczas implementowania [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości "otoki" Upewnij się, że zbyt otoki nie ma implementacji zestawu, tak że nie są w stanie tylko do odczytu dla publicznych otoki niezgodności ujawnia.  
  
-   Obiekt zwrócony przez rejestracja tylko do odczytu jest <xref:System.Windows.DependencyPropertyKey> zamiast <xref:System.Windows.DependencyProperty>. Nadal należy przechowywać w tym polu jako element członkowski, ale zazwyczaj można nie spowoduje publicznego elementu członkowskiego typu.  
  
 Niezależnie od prywatnej pola lub wartość ma zapasowy z właściwości tylko do odczytu zależności oczywiście można pełni zapisu przy użyciu logiki, niezależnie od podjęcia decyzji. Jednak jest najbardziej oczywistym sposobem ustaw właściwość początkowo lub jako część logiki środowiska uruchomieniowego do korzystania z systemu właściwości [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], zamiast obejścia system właściwości i ustawienie pola zapasowego prywatnego bezpośrednio. W szczególności jest podpis <xref:System.Windows.DependencyObject.SetValue%2A> który akceptuje parametr typu <xref:System.Windows.DependencyPropertyKey>. Jak i gdzie tę wartość ustawiono programowo w aplikacji logiki będzie miało wpływ na sposób możesz ustawić dostęp na <xref:System.Windows.DependencyPropertyKey> utworzone przy pierwszej rejestracji właściwości zależności. Jeśli obsługiwać tę logikę w klasie można wprowadzić prywatnych lub wymagane ustawienie z innych części zestawu może być ustawiony wewnętrznego. Jednym z podejść jest wywołanie <xref:System.Windows.DependencyObject.SetValue%2A> w obrębie klasy obsługi zdarzenia odpowiednie zdarzenia, które informują wystąpienia klasy, która musi zostać zmienione wartości właściwości przechowywanej. Innym rozwiązaniem jest powiązanie właściwości zależności ze sobą za pomocą łączyć <xref:System.Windows.PropertyChangedCallback> i <xref:System.Windows.CoerceValueCallback> wywołania zwrotne w ramach tych właściwości metadanych podczas rejestracji.  
  
 Ponieważ <xref:System.Windows.DependencyPropertyKey> jest prywatny i nie są propagowane w systemie właściwości poza swój kod, właściwości tylko do odczytu zależności mają lepiej ustawienie zabezpieczeń niż właściwości zależności odczytu i zapisu. Dla właściwości zależności odczytu i zapisu pole identyfikacyjne jest jawnie lub niejawnie publicznego i w związku z tym jest powszechnie można ustawić właściwości. Aby uzyskać więcej szczegółowych informacji, zobacz [zabezpieczeń właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
