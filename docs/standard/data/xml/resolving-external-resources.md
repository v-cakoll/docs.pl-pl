---
title: Rozpoznawanie zasobów zewnętrznych
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
ms.openlocfilehash: 05cc41cef7da07581d4f0ec8e584858b913d1a80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710274"
---
# <a name="resolving-external-resources"></a>Rozpoznawanie zasobów zewnętrznych
Właściwość **XmlResolver** obiektu **XmlDocument** jest używana przez klasę **XmlDocument** do lokalizowania zasobów, które nie są wbudowane w dane XML, takie jak definicje typu dokumentu zewnętrznego (DTD), jednostki i schematy. Elementy te mogą znajdować się w sieci lub na dysku lokalnym i są identyfikowane za pomocą Uniform Resource Identifier (URI). Dzięki temu element **XmlDocument** może rozpoznać węzły **EntityReference** , które znajdują się w dokumencie i sprawdzać poprawność dokumentu zgodnie z zewnętrznym DTD lub schematem.  
  
## <a name="fully-trusted-xmldocument"></a>W pełni zaufany dokument XmlDocument  
 Właściwość **XmlResolver** ma wpływ na funkcjonalność metody **XmlDocument. Load** . W poniższej tabeli pokazano, jak działa Właściwość **XmlDocument. XmlResolver** , gdy obiekt **XmlDocument** jest w pełni zaufany. W poniższej tabeli przedstawiono metody **XmlDocument. Load** , gdy dane wejściowe do obciążenia to **TextReader**, **ciąg**, **strumień**lub **Identyfikator URI**. Ta tabela nie ma zastosowania do metody **Load** , jeśli element **XmlDocument** jest ładowany z elementu **XmlReader**.  
  
|XmlResolver — właściwość|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|Właściwość jest ustawiona na klasę **XmlResolver** , która została wcześniej utworzona i ma właściwości, które zostały już ustawione przez użytkownika.|**XmlDocument** używa **XmlResolver** , który jest rozpoznawany do rozpoznawania nazw plików, do rozpoznawania odwołań do zasobów zewnętrznych, takich jak definicje DTD, jednostki i schematy.<br /><br /> Element **XmlResolver** jest również używany podczas rozpoznawania zasobów zewnętrznych, które są zbędne podczas dodawania lub edytowania węzłów w **XmlDocument**.|Element **XmlResolver** przyznany dla **dokumentu XmlDocument** jest mechanizmem rozwiązywania konfliktów używanym do znajdowania i rozwiązywania zasobów zewnętrznych.|  
|Właściwość ma wartość **null** (**Nothing** w programie Microsoft Visual Basic .NET).|Funkcje, które wymagają zasobu zewnętrznego, nie są obsługiwane, takie jak lokalizowanie zewnętrznego schematu lub DTD. Nie są obsługiwane żadne jednostki zewnętrzne ani funkcje edycji, takie jak wstawianie węzłów jednostek, które wymagają rozwiązania.|**Dokument XmlDocument** ładuje pliki jako anonimowe i nie próbuje rozwiązać żadnych innych zasobów.|  
|Właściwość nie jest ustawiona, ale pozostaje w stanie domyślnym.|**XmlUrlResolver** z poświadczeniami o wartości null zostanie utworzona i użyta przez **XmlDocument** podczas rozpoznawania nazw plików, lokalizowanie zewnętrznych elementów DTD, jednostek i schematów, a poświadczenia o **wartości null** są używane podczas edytowania węzłów.||  
  
 W poniższej tabeli przedstawiono metodę **XmlDocument. Load** , gdy dane wejściowe **ładowania** są element **XmlReader** , a element **XmlDocument** jest w pełni zaufany.  
  
|XmlResolver — właściwość|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|Klasa **XmlResolver** używana przez **XmlDocument** jest tą samą klasą, która jest używana przez element **XmlReader**.|**XmlDocument** używa elementu **XmlResolver** , który został przypisany do elementu **XmlReader**.<br /><br /> Nie można ustawić właściwości **XmlDocument. resolver** , niezależnie od poziomu zaufania **XmlDocument** , ponieważ jest ona pobierana z elementu **XmlReader** **XmlResolver** . Nie można podjąć próby przesłonięcia ustawień **Xmlresolvera** **XmlReader**, ustawiając właściwość **XmlResolver** obiektu **XmlDocument**.|Element **XmlReader** może być **XmlTextReader**, **XmlValidatingReader**lub czytnikiem niestandardowym. Jeśli używany czytnik obsługuje rozpoznawanie jednostek, jednostki zewnętrzne są rozwiązane. Jeśli czytnik nie obsługuje odwołań do jednostek, odwołania do jednostek nie są rozwiązywane.|  
  
## <a name="semi-trusted-xmldocument"></a>Częściowo zaufany dokument XmlDocument  
 W poniższej tabeli pokazano, jak działa Właściwość **XmlDocument. XmlResolver** , gdy obiekt jest częściowo zaufany. Ta tabela ma zastosowanie do metod **XmlDocument. Load** , gdy dane wejściowe ładowania to **TextReader**, **String**, **Stream**lub **URI**. Ta tabela nie ma zastosowania do metody **Load** , jeśli element **XmlDocument** jest ładowany z elementu **XmlReader**.  
  
|XmlResolver — właściwość|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|W przypadku scenariusza częściowo zaufanego Właściwość **XmlResolver** nie może być ustawiona na wartość inną niż null.|**XmlUrlResolver** z poświadczeniami o **wartości null** zostanie utworzona i użyta przez **XmlDocument** podczas rozpoznawania nazw plików, lokalizowanie zewnętrznych elementów DTD, jednostek i schematów, a poświadczenia o **wartości null** są używane podczas edytowania węzłów.|Takie zachowanie jest takie samo jak zachowanie, gdy właściwość **XmlResolver** nie jest ustawiona, ale pozostawiono w stanie domyślnym.<br /><br /> **XmlDocument** używa uprawnień anonimowych dla wszystkich akcji.|  
|Właściwość ma wartość **null** (**Nothing** w programie Microsoft Visual Basic .NET).|Nie są obsługiwane żadne funkcje, które wymagają zasobu zewnętrznego, takie jak lokalizowanie zewnętrznego schematu lub DTD. Nie są obsługiwane żadne jednostki zewnętrzne ani funkcje edycji, takie jak wstawianie węzłów jednostek, które wymagają rozwiązania.|Gdy właściwość ma **wartość null**, zachowanie jest takie samo niezależnie od tego, czy **dokument XmlDocument** jest w pełni zaufany, czy częściowo zaufany.|  
|Właściwość nie jest ustawiona, ale pozostaje w stanie domyślnym.|**XmlUrlResolver** z poświadczeniami o **wartości null** zostanie utworzona i użyta przez **XmlDocument** podczas rozpoznawania nazw plików, lokalizowanie zewnętrznych elementów DTD, jednostek i schematów, a poświadczenia o **wartości null** są używane podczas edytowania węzłów.|**XmlDocument** używa uprawnień anonimowych dla wszystkich akcji.|  
  
 Ta tabela ma zastosowanie do metody **XmlDocument. Load** , gdy dane wejściowe do **obciążenia** to element **XmlReader**, a element **XmlDocument** jest częściowo zaufany.  
  
|XmlResolver — właściwość|Funkcja|Uwagi|  
|--------------------------|--------------|-----------|  
|Klasa **XmlResolver** używana przez **XmlDocument** jest taka sama jak ta, która jest używana przez element **XmlReader**.|**XmlDocument** używa elementu **XmlResolver** , który został przypisany do elementu **XmlReader**.<br /><br /> Nie można ustawić właściwości **XmlDocument. resolver** , niezależnie od poziomu zaufania **XmlDocument** , ponieważ jest ona pobierana z elementu **XmlReader** **XmlResolver** . Nie można podjąć próby przesłonięcia ustawień elementu **XmlResolver xmlrozpoznawania** , ustawiając właściwość **XmlResolver** obiektu **XmlDocument**.|Element **XmlReader** może być **XmlTextReader**, walidacją <xref:System.Xml.XmlReader>lub czytnikiem niestandardowym. Jeśli używany czytnik obsługuje rozpoznawanie jednostek, jednostki zewnętrzne są rozwiązane. Jeśli czytnik programu przeszedł nie obsługuje odwołań do jednostek, odwołania do jednostek nie są rozwiązane.|  
  
 Ustawienie XmlResolver w taki sposób, aby zawierało poprawne poświadczenia, umożliwia dostęp do zasobów zewnętrznych.  
  
> [!NOTE]
> Nie ma możliwości pobrania właściwości **XmlResolver** . Pozwala to zapobiec użyciu przez użytkownika elementu **XmlResolver** , na którym zostały ustawione poświadczenia. Ponadto jeśli **XmlTextReader** lub walidacja <xref:System.Xml.XmlReader> jest używana do załadowania **dokumentu** XmlDocument, a element **XmlDocument** ma skonfigurowany mechanizm rozwiązywania konfliktów, nie są buforowane przez **XmlDocument** po fazie **obciążenia** , ponieważ stanowi to również zagrożenie bezpieczeństwa.  
  
 Aby uzyskać więcej informacji, zobacz sekcję uwagi na stronie odniesienia <xref:System.Xml.XmlResolver>.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
