---
title: Zabezpieczenie właściwości zależności
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: 2f9de32eb8637e58c17aba2309eed33dcfdd42a7
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400769"
---
# <a name="dependency-property-security"></a>Zabezpieczenie właściwości zależności
Właściwości zależności powinny być zwykle uznawane za właściwości publiczne. Charakter [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systemu właściwości uniemożliwia możliwość podejmowania gwarancji bezpieczeństwa dotyczących wartości właściwości zależności.  

<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Dostęp i zabezpieczenia otok i właściwości zależności  
 Zazwyczaj właściwości zależności są implementowane wraz z właściwościami "otoka" środowiska uruchomieniowego języka wspólnego (CLR), które upraszczają pobieranie lub Ustawianie właściwości z wystąpienia. Jednak otoki są naprawdę tylko wygodnymi metodami, które implementują <xref:System.Windows.DependencyObject.SetValue%2A> wywołania bazowe <xref:System.Windows.DependencyObject.GetValue%2A> i statyczne, które są używane podczas współpracy z właściwościami zależności. Zastanawiasz się, że właściwości są uwidocznione jako właściwości środowiska uruchomieniowego języka wspólnego (CLR), które mają być chronione przez właściwość zależności, a nie za pomocą pola prywatnego. Mechanizmy zabezpieczeń stosowane do otok nie są równoległe do zachowania systemu właściwości i dostępu do podstawowej właściwości zależności. Umieszczenie wymaganego poziomu zabezpieczeń w otoki uniemożliwi użycie wygody metody, ale nie uniemożliwi wywoływania <xref:System.Windows.DependencyObject.GetValue%2A> lub. <xref:System.Windows.DependencyObject.SetValue%2A> Analogicznie, umieszczenie chronionego lub prywatnego poziomu dostępu do otok nie zapewnia żadnych skutecznych zabezpieczeń.  
  
 W przypadku pisania własnych właściwości zależności należy zadeklarować otoki i <xref:System.Windows.DependencyProperty> pole identyfikatora jako publiczne elementy członkowskie, tak aby wywołujący nie pobierali mylących informacji o prawdziwym poziomie dostępu do tej właściwości (ze względu na to, że magazyn jest zaimplementowane jako właściwość zależności).  
  
 Dla właściwości zależności niestandardowej można zarejestrować właściwość jako właściwość zależności tylko <xref:System.Windows.DependencyPropertyKey> do odczytu, co zapewnia efektywne środki uniemożliwiające ustawienie właściwości przez każdą osobę, która nie przechowuje odwołania do tej właściwości. Aby uzyskać więcej informacji, zobacz [właściwości zależności tylko do odczytu](read-only-dependency-properties.md).  
  
> [!NOTE]
>  Deklarowanie <xref:System.Windows.DependencyProperty> pola identyfikatora Private nie jest zabronione i można go wykorzystać, aby zmniejszyć bezpośrednio uwidocznioną przestrzeń nazw klasy niestandardowej, ale taka właściwość nie powinna być traktowana jako "Private" w tym samym sensie jak w przypadku wspólnego języka definicje języka środowiska uruchomieniowego (CLR) definiują ten poziom dostępu z powodów opisanych w następnej sekcji.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Wyeksponowanie właściwości zależności przez system właściwości  
 Nie jest to ogólnie przydatne i potencjalnie mylące, aby zadeklarować <xref:System.Windows.DependencyProperty> jako dowolny poziom dostępu inny niż publiczny. Ustawienie poziomu dostępu uniemożliwia innym osobom uzyskanie odwołania do wystąpienia z klasy deklarującej. Ale istnieje kilka aspektów systemu właściwości, które zwracają <xref:System.Windows.DependencyProperty> jako środek identyfikacji konkretnej właściwości, która istnieje w wystąpieniu klasy lub wystąpienia klasy pochodnej i ten identyfikator nadal można użyć <xref:System.Windows.DependencyObject.SetValue%2A> w wywołaniu nawet Jeśli oryginalny identyfikator statyczny jest zadeklarowany jako niepubliczny. Ponadto metody <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> wirtualne otrzymują informacje o istniejącej właściwości zależności, która zmieniła wartość. Ponadto <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> Metoda zwraca identyfikatory dla każdej właściwości w wystąpieniach o wartości ustawionej lokalnie.  
  
### <a name="validation-and-security"></a>Sprawdzanie poprawności i zabezpieczenia  
 Zastosowanie żądania do <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> i oczekiwanie na niepowodzenie walidacji na żądanie, aby zapobiec ustawianiu właściwości, nie jest odpowiednim mechanizmem zabezpieczeń. Sprawdzanie poprawności wartości ustawionej za pomocą <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> może być również pomijane przez złośliwych wywołujących, jeśli te obiekty wywołujące działają w domenie aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
