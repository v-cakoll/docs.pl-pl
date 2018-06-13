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
ms.openlocfilehash: 825b2a3dc79300f0cc26514398b8de0abee64fd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540507"
---
# <a name="dependency-property-security"></a>Zabezpieczenie właściwości zależności
Właściwości zależności zazwyczaj należy traktować jako właściwości publiczne. Rodzaj [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systemu właściwość zapobiega możliwości gwarancje bezpieczeństwa o wartość właściwości zależności.  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Dostęp i większe bezpieczeństwo otoki i właściwości zależności  
 Zazwyczaj właściwości zależności są implementowane wraz z "otoki" [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości, które upraszczają pobierania lub ustawiania właściwości z wystąpienia. Ale otoki są naprawdę tylko podręczne metody, które implementują odpowiadającego <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> statyczne wywołania, które są używane podczas interakcji z właściwości zależności. Myśląc jej w inny sposób, właściwości są widoczne jako [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości, które się zdarzyć, aby była obsługiwana przez właściwości zależności, a nie przez pole prywatne. Mechanizmy zabezpieczeń stosowane do otoki nie równoległe właściwości systemu zachowania i dostępu właściwości zależności. Żądania zabezpieczeń do obrotu otoka tylko uniemożliwi użycie metody wygody, ale nie uniemożliwia wywołań <xref:System.Windows.DependencyObject.GetValue%2A> lub <xref:System.Windows.DependencyObject.SetValue%2A>. Podobnie umieszczenie chroniona lub poziom dostępu prywatnego otoki nie ma żadnych efektywnym elementem systemu zabezpieczeń.  
  
 Jeśli piszesz właściwości zależności powinny deklarować otoki i <xref:System.Windows.DependencyProperty> identyfikatora pola jako publiczne elementy członkowskie, dzięki czemu wywołań nie pobrać nieprawdziwych informacji o poziomie wartość true, dostęp do tej właściwości (ze względu na jego magazynu jest zaimplementowane jako właściwość zależności).  
  
 Dla właściwości zależności niestandardowych, można zarejestrować Twoje właściwości jako właściwość zależności tylko do odczytu, a to zapewnić skuteczne środki zapobieganie ustawiona przez każdy użytkownik, który nie zawiera odwołania do <xref:System.Windows.DependencyPropertyKey> dla tej właściwości. Aby uzyskać więcej informacji, zobacz [tylko do odczytu właściwości zależności](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
> [!NOTE]
>  Deklarowanie <xref:System.Windows.DependencyProperty> prywatnego pola Identyfikator nie jest zabroniona, można umieścić służyć do zmniejszenia natychmiast narażonych przestrzeni nazw, klasy niestandardowej, ale taka właściwość nie należy traktować jako "prywatny" w tym samym znaczeniu jako [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] Język definicji zdefiniuj tego poziomu dostępu powodów opisanych w następnej sekcji.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Właściwości systemu ujawnienia właściwości zależności  
 Nie jest to zazwyczaj przydatne i jest potencjalnie mylący, aby zadeklarować <xref:System.Windows.DependencyProperty> jako dowolny dostęp na poziomie innych niż publicznego. Ustawienie poziomu dostępu tylko zapobiega ktoś mógł uzyskać odwołania do wystąpienia klasy deklarujący. Jednak kilka aspektów systemu właściwość, która zwróci <xref:System.Windows.DependencyProperty> jako sposób identyfikowania określonej właściwości znajduje się ona na wystąpienie klasy lub wystąpienia klasy pochodnej, a ten identyfikator jest wciąż można jej użyć w <xref:System.Windows.DependencyObject.SetValue%2A> nawet wywołania Jeśli oryginalny identyfikator statycznego jest zadeklarowany jako nonpublic. Ponadto <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> metody wirtualne otrzymywanie informacji żadnych istniejących właściwości zależności, zmienić wartość. Ponadto <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> metoda zwraca identyfikatory dla każdej właściwości w wystąpieniach lokalnie ustawionej wartości.  
  
### <a name="validation-and-security"></a>Sprawdzanie poprawności i zabezpieczeń  
 Żądanie do stosowania <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> i oczekiwano niepowodzenia weryfikacji w przypadku niepowodzenia żądanie, aby zapobiec ustawiania właściwości nie jest mechanizm odpowiednich zabezpieczeń. Ustaw wartość unieważniania wymuszane za pośrednictwem <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> również mogła zostać pominięta przez złośliwe obiekty wywołujące, jeśli tych wywołań działają w ramach domeny aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
