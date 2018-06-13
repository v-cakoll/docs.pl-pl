---
title: Rozpoznawanie zewnętrznych zasobów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1c56d69724212b9d1cd6a24204a12460071633f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577105"
---
# <a name="resolving-external-resources"></a>Rozpoznawanie zewnętrznych zasobów
**Element XmlResolver** właściwość **XmlDocument** jest używany przez **XmlDocument** klasy lokalizowanie zasobów, które nie są wbudowane w danych XML, takie jak typ dokumentu zewnętrznego definicje (elementów DTD), jednostki i schematów. Te elementy mogą znajdować się w sieci lub na lokalnym dysku i zidentyfikować przez zasób identyfikator URI (Uniform). Dzięki temu **XmlDocument** rozwiązywać **EntityReference** węzłów, które znajdują się w dokumencie i walidacji dokumentu zgodnie z zewnętrzna definicja DTD lub schemat.  
  
## <a name="fully-trusted-xmldocument"></a>Pełni zaufanych XmlDocument  
 **Element XmlResolver** właściwość ma wpływ na funkcjonalność **XmlDocument.Load** metody. Poniższa tabela pokazuje sposób **XmlDocument.XmlResolver** właściwości działa, kiedy **XmlDocument** obiekt jest w pełni zaufany. W poniższej tabeli przedstawiono **XmlDocument.Load** metody, gdy dane wejściowe obciążenia są **TextReader**, **ciąg**, **strumienia**, lub  **Identyfikator URI**. Ta tabela nie ma zastosowania do **obciążenia** metody Jeśli **XmlDocument** został załadowany z **XmlReader**.  
  
|Element XmlResolver właściwości|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|Właściwość jest ustawiona na **element XmlResolver** klasy, która została wcześniej utworzona i ustawiono już na nim przez użytkownika ani właściwości.|**XmlDocument** używa **element XmlResolver** który znajduje się do rozpoznawania nazw plików, można rozpoznać odwołania do zasobów zewnętrznych, takich jak pliki DTD, jednostki i schematów.<br /><br /> **Element XmlResolver** jest również używany podczas rozpoznawania zasobów zewnętrznych, które są wymagane podczas dodawania lub edycji węzłów w **XmlDocument**.|**Element XmlResolver** do **XmlDocument** jest program rozpoznawania nazw, która jest używana zawsze, gdy zasobów zewnętrznych muszą być znajduje się i rozwiązać.|  
|Właściwość jest ustawiona na **null** (**nic** języka Microsoft Visual Basic .NET).|Funkcje, które wymagają zasób zewnętrzny nie są obsługiwane, takich jak lokalizowanie zewnętrzny schemat lub definicji DTD. Nie podmiotów zewnętrznych zostanie rozwiązany i wykonywania edycji funkcji, takich jak wstawianie węzłów jednostki, które wymagają rozdzielczości, nie są obsługiwane.|**XmlDocument** ładunków pliki jako anonimowy i nie jest podejmowana próba rozpoznania żadnych innych zasobów.|  
|Właściwość nie jest ustawiona, ale pozostanie w stanie domyślnym.|**XmlUrlResolver** z wartością NULL poświadczeń zostanie utworzone i używane przez **XmlDocument** podczas rozpoznawania nazw plików, lokalizowania zewnętrznej definicji DTD, jednostki i schematów, a **wartościnull** poświadczenia są używane podczas edytowania węzłów.||  
  
 W poniższej tabeli przedstawiono **XmlDocument.Load** metody gdy dane wejściowe **obciążenia** jest **XmlReader** i **XmlDocument** jest pełni zaufany.  
  
|Element XmlResolver właściwości|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|**Element XmlResolver** klasy używane przez **XmlDocument** jest tej samej klasy używane przez **XmlReader**.|**XmlDocument** używa **element XmlResolver** która została przypisana do **XmlReader**.<br /><br /> **XmlDocument.Resolver** właściwość nie może być ustawiona, niezależnie od tego, **XmlDocument** poziom, zaufania, ponieważ jest ona pobieranie **element XmlResolver** z  **Element XmlReader**. Nie ma możliwości zastępują ustawienia **XmlReaders**" **element XmlResolver** przez ustawienie **element XmlResolver** właściwość **XmlDocument**.|**XmlReader** może być **XmlTextReader**, **elementu XmlValidatingReader**, lub czytnika zapisywane niestandardowe. Jeśli użyto czytnika obsługuje jednostki, zostaną rozpoznane podmiotów zewnętrznych. Jeśli czytnik przekazany nie obsługuje odwołań do jednostek, następnie obiekt, do którego odwołuje się do nie są rozpoznawane.|  
  
## <a name="semi-trusted-xmldocument"></a>Częściowo zaufane XmlDocument  
 W poniższej tabeli przedstawiono sposób **XmlDocument.XmlResolver** właściwości działa, gdy obiekt jest częściowo zaufany. Ta tabela odnosi się do **XmlDocument.Load** metody, gdy dane wejściowe obciążenia są **TextReader**, **ciąg**, **strumienia**, lub  **Identyfikator URI**. Ta tabela nie ma zastosowania do **obciążenia** metody Jeśli **XmlDocument** został załadowany z **XmlReader**.  
  
|Element XmlResolver właściwości|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|W tym scenariuszu częściowo zaufany **element XmlResolver** właściwości nie można ustawić na wartość inną niż null.|**XmlUrlResolver** z **null** poświadczeń zostanie utworzone i będzie używana przez **XmlDocument** podczas rozpoznawania nazwy plików w lokalizacji zewnętrznej definicji DTD, jednostek, a schematy, i **null** poświadczenia są używane podczas edytowania węzłów.|To zachowanie jest takie same jak zachowanie podczas **element XmlResolver** właściwość nie jest ustawiona, ale pozostanie w stanie domyślnym.<br /><br /> **XmlDocument** używa uprawnień dla wszystkich akcji.|  
|Właściwość jest ustawiona na **null** (**nic** języka Microsoft Visual Basic .NET).|Nie funkcje, które wymagają zewnętrzny zasób są obsługiwane, takich jak lokalizowanie zewnętrzny schemat lub definicji DTD. Ani podmiotów zewnętrznych zostanie rozwiązany, i wykonywanie edycji funkcji, takich jak wstawianie węzłów jednostki, które wymagają rozdzielczości, nie są obsługiwane.|Gdy ta właściwość jest **null**, zachowanie jest tym samym niezależnie od tego, jeśli **XmlDocument** jest w pełni zaufanym lub częściowo zaufany.|  
|Właściwość nie jest ustawiona, ale pozostanie w stanie domyślnym.|**XmlUrlResolver** z **null** poświadczeń zostanie utworzone i będzie używana przez **XmlDocument** podczas rozpoznawania nazwy plików w lokalizacji zewnętrznej definicji DTD, jednostek, a schematy, i **null** poświadczenia są używane podczas edytowania węzłów.|**XmlDocument** używa uprawnień dla wszystkich akcji.|  
  
 Ta tabela odnosi się do **XmlDocument.Load** metody gdy dane wejściowe **obciążenia** jest **XmlReader**i **XmlDocument** jest częściowo zaufany.  
  
|Element XmlResolver właściwości|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|**Element XmlResolver** klasy używane przez **XmlDocument** jest taka sama jak używany przez **XmlReader**.|**XmlDocument** używa **element XmlResolver** która została przypisana do **XmlReader**.<br /><br /> **XmlDocument.Resolver** właściwość nie może być ustawiona, niezależnie od tego, **XmlDocument** poziom, zaufania, ponieważ jest ona pobieranie **element XmlResolver** z  **Element XmlReader**. Nie ma możliwości zastępują ustawienia **XmlReaders** **element XmlResolver** przez ustawienie **element XmlResolver** właściwość **XmlDocument**.|**XmlReader** może być **XmlTextReader**, sprawdzanie poprawności <xref:System.Xml.XmlReader>, lub czytnika zapisywane niestandardowe. Jeśli użyto czytnika obsługuje jednostki, zostaną rozpoznane podmiotów zewnętrznych. Jeśli czytnik przekazano nie obsługuje odwołań do jednostek, odwołań do jednostek nie są rozpoznawane.|  
  
 Ustawienie element XmlResolver zawiera poprawne poświadczenia zezwala na dostęp do zasobów zewnętrznych.  
  
> [!NOTE]
>  Nie istnieje sposób pobrać **element XmlResolver** właściwości. Dzięki temu można uniemożliwić użytkownikowi ponowne używanie **element XmlResolver** poświadczeń, które zostały ustawione. Ponadto jeśli **XmlTextReader** lub sprawdzania poprawności <xref:System.Xml.XmlReader> jest używana do załadowania **XmlDocument** i **XmlDocument** ma program rozpoznawania nazw, która została ustawiona, rozpoznawania nazw z takie czytniki nie są obsługiwane przez **XmlDocument** po **obciążenia** fazy, ponieważ to również stanowi zagrożenie bezpieczeństwa.  
  
 Aby uzyskać więcej informacji, zobacz sekcję uwag <xref:System.Xml.XmlResolver> strony odwołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
