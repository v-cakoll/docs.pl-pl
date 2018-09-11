---
title: Rozpoznawanie zewnętrznych zasobów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef31d101769dca00f5cff545c72b3afbd59bc638
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268409"
---
# <a name="resolving-external-resources"></a>Rozpoznawanie zewnętrznych zasobów
**Element XmlResolver** właściwość **XmlDocument** jest używany przez **XmlDocument** klasy do lokalizowania zasobów, które nie są wbudowane w danych XML, takie jak typ dokumentu zewnętrznego definicje (pliki DTD), jednostki i schematów. Te elementy można znaleźć w sieci lub na dysku lokalnym i są oznaczone przez jednolite zasobów identyfikator (URI). Dzięki temu **XmlDocument** rozpoznać **EntityReference** węzły, które znajdują się w dokumencie i sprawdź poprawność dokumentu zgodnie z zewnętrzna definicja DTD lub schematu.  
  
## <a name="fully-trusted-xmldocument"></a>W pełni zaufane XmlDocument  
 **Element XmlResolver** właściwość ma wpływ na funkcjonalność **XmlDocument.Load** metody. Poniższa tabela pokazuje sposób, w jaki **XmlDocument.XmlResolver** właściwości działa, kiedy **XmlDocument** obiekt jest w pełni zaufany. W poniższej tabeli przedstawiono **XmlDocument.Load** metody, gdy dane wejściowe do obciążenia **TextReader**, **ciąg**, **Stream**, lub  **Identyfikator URI**. Ta tabela nie ma zastosowania do **obciążenia** metoda Jeśli **XmlDocument** jest ładowany z **XmlReader**.  
  
|Element XmlResolver właściwości|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|Właściwość jest ustawiona na **element XmlResolver** klasy, która została utworzona wcześniej i ma właściwości, które już ustawiony przez użytkownika.|**XmlDocument** używa **element XmlResolver** , umożliwiającej rozpoznawanie nazw plików, do rozpoznawania odwołań do zasobów zewnętrznych, takich jak pliki DTD, jednostek i schematów.<br /><br /> **Element XmlResolver** jest również używany podczas rozpoznawanie zasobów zewnętrznych, które są wymagane podczas dodawania lub edytowania węzłów w **XmlDocument**.|**Element XmlResolver** umożliwiającej **XmlDocument** jest rozpoznawania nazw, która jest używana zawsze, gdy zasoby zewnętrzne muszą być znajduje się i usunięciu.|  
|Właściwość jest ustawiona na **null** (**nic** w Microsoft Visual Basic .NET).|Funkcje, które wymagają zewnętrznego zasobu nie są obsługiwane, takich jak znajdowanie zewnętrzny schemat lub DTD. Ani podmiotów zewnętrznych zostanie rozwiązany, a wykonywanie edycji funkcje, takie jak wstawianie węzłów jednostki, które wymagają rozwiązania, nie są obsługiwane.|**XmlDocument** ładowania plików jako anonimowy i nie próbuje rozpoznać wszystkich innych zasobów.|  
|Właściwość nie jest ustawiona, ale pozostanie w stanie domyślnym.|**XmlUrlResolver** z wartością NULL poświadczenia będą tworzone i używane przez **XmlDocument** podczas rozpoznawania nazwy plików w lokalizacji zewnętrznej definicji DTD, jednostek i schematy, i **wartościnull** poświadczenia są używane podczas edytowania węzłów.||  
  
 W poniższej tabeli przedstawiono **XmlDocument.Load** metoda gdy dane wejściowe **obciążenia** jest **XmlReader** i **XmlDocument** jest w pełni zaufany.  
  
|Element XmlResolver właściwości|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|**Element XmlResolver** używane przez klasy **XmlDocument** jest tej samej klasy, które są używane przez **XmlReader**.|**XmlDocument** używa **element XmlResolver** który został przypisany do **XmlReader**.<br /><br /> **XmlDocument.Resolver** właściwość nie może być ustawiona, niezależnie od tego, **XmlDocument** poziomu zaufania, ponieważ stają się coraz **element XmlResolver** z  **Element XmlReader**. Nie ma możliwości zastąpienia ustawień **XmlReaders**" **element XmlResolver** , ustawiając **element XmlResolver** właściwość **XmlDocument**.|**XmlReader** może być **klasy XmlTextReader**, **elementu XmlValidatingReader**, lub czytnika zapisywane niestandardowe. Jeśli czytnika obsługuje rozpoznawanie jednostek, są rozwiązywane podmiotów zewnętrznych. Jeśli przekazywana czytnik nie obsługuje odwołań do jednostek, następnie obiekt, do którego odwołania nie są rozpoznawane.|  
  
## <a name="semi-trusted-xmldocument"></a>Częściowo zaufanych XmlDocument  
 W poniższej tabeli przedstawiono sposób, w jaki **XmlDocument.XmlResolver** właściwości działa, gdy obiekt jest częściowo zaufany. Ta tabela ma zastosowanie do **XmlDocument.Load** metody, gdy dane wejściowe do obciążenia **TextReader**, **ciąg**, **Stream**, lub  **Identyfikator URI**. Ta tabela nie ma zastosowania do **obciążenia** metoda Jeśli **XmlDocument** jest ładowany z **XmlReader**.  
  
|Element XmlResolver właściwości|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|W tym scenariuszu wpół zaufanych **element XmlResolver** właściwości nie można ustawić na wartość inną niż null.|**XmlUrlResolver** z **null** poświadczenia będą tworzone i używane przez **XmlDocument** podczas rozpoznawania nazwy plików w lokalizacji zewnętrznej definicji DTD, jednostki i schematy, i **null** poświadczenia są używane podczas edytowania węzłów.|To zachowanie jest identyczne z zachowaniem podczas **element XmlResolver** właściwość nie jest ustawiona, ale pozostanie w stanie domyślnym.<br /><br /> **XmlDocument** używa uprawnień dla wszystkich akcji.|  
|Właściwość jest ustawiona na **null** (**nic** w Microsoft Visual Basic .NET).|Żadne funkcje, wymagające zewnętrznego zasobu są obsługiwane, takich jak znajdowanie zewnętrzny schemat lub DTD. Ani podmiotów zewnętrznych zostanie rozwiązany, a wykonywanie edycji funkcji, takich jak wstawianie węzłów jednostki, które wymagają rozwiązania, nie są obsługiwane.|Jeśli właściwość jest **null**, zachowanie jest identyczny, niezależnie od tego, jeśli **XmlDocument** jest w pełni zaufany lub na wpół zaufanych.|  
|Właściwość nie jest ustawiona, ale pozostanie w stanie domyślnym.|**XmlUrlResolver** z **null** poświadczenia będą tworzone i używane przez **XmlDocument** podczas rozpoznawania nazwy plików w lokalizacji zewnętrznej definicji DTD, jednostki i schematy, i **null** poświadczenia są używane podczas edytowania węzłów.|**XmlDocument** używa uprawnień dla wszystkich akcji.|  
  
 Ta tabela ma zastosowanie do **XmlDocument.Load** metoda gdy dane wejściowe **obciążenia** jest **XmlReader**i **XmlDocument** jest częściowo zaufany.  
  
|Element XmlResolver właściwości|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|**Element XmlResolver** używane przez klasy **XmlDocument** jest on używany przez **XmlReader**.|**XmlDocument** używa **element XmlResolver** który został przypisany do **XmlReader**.<br /><br /> **XmlDocument.Resolver** właściwość nie może być ustawiona, niezależnie od tego, **XmlDocument** poziomu zaufania, ponieważ stają się coraz **element XmlResolver** z  **Element XmlReader**. Nie ma możliwości zastąpienia ustawień **XmlReaders** **element XmlResolver** , ustawiając **element XmlResolver** właściwość **XmlDocument**.|**XmlReader** może być **klasy XmlTextReader**, sprawdzanie poprawności <xref:System.Xml.XmlReader>, lub czytnika zapisywane niestandardowe. Jeśli czytnika obsługuje rozpoznawanie jednostek, są rozwiązywane podmiotów zewnętrznych. Jeśli czytnik przekazanej nepodporuje odkazy entit, odwołania do jednostek nie są rozpoznawane.|  
  
 Ustawiając element XmlResolver zawiera poprawne poświadczenia umożliwia dostęp do zasobów zewnętrznych.  
  
> [!NOTE]
>  Nie istnieje sposób pobrać **element XmlResolver** właściwości. Pomaga to uniemożliwić użytkownikowi ponowne używanie **element XmlResolver** poświadczeń, które zostały ustawione. Ponadto jeśli **klasy XmlTextReader** lub sprawdzania poprawności <xref:System.Xml.XmlReader> jest używana do ładowania **XmlDocument** i **XmlDocument** ma program rozpoznawania nazw, która została ustawiona, rozpoznawania nazw z takie czytniki nie są buforowane przez **XmlDocument** po **obciążenia** fazy, ponieważ również stwarza zagrożenie dla bezpieczeństwa.  
  
 Aby uzyskać więcej informacji, zobacz sekcję Uwagi <xref:System.Xml.XmlResolver> odwołania do stron.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
