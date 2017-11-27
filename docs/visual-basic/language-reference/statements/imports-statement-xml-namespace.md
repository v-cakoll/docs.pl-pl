---
title: "Imports — Instrukcja (przestrzeń nazw XML)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0fe6d37c58ead94f2c03736318209abb67cd6dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imports-statement-xml-namespace"></a>Imports — Instrukcja (przestrzeń nazw XML)
Importuje prefiksy przestrzeni nazw XML do użycia w literałach XML i właściwości osi XML.  
  
## <a name="syntax"></a>Składnia  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>Części  
 `xmlNamespacePrefix`  
 Opcjonalny. Ciąg XML, które elementy i atrybuty mogą odwoływać się do `xmlNamespaceName`. Jeśli nie `xmlNamespacePrefix` jest podany, importowanych przestrzeni nazw XML jest domyślna przestrzeń nazw XML. Musi być prawidłowym identyfikatorem XML. Aby uzyskać więcej informacji, zobacz [nazwy z zadeklarowany elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  
  
 `xmlNamespaceName`  
 Wymagany. Ciąg identyfikujący importowanych przestrzeni nazw XML.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `Imports` instrukcji, aby zdefiniować globalnej przestrzeni nazw XML, korzystających z literały XML i właściwości osi XML lub przekazywane jako parametry do `GetXmlNamespace` operatora. (Aby uzyskać informacje o korzystaniu z `Imports` instrukcji, aby zaimportować alias, który może służyć, których nazwy typów są używane w kodzie, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Składnia deklaracji przestrzeni nazw XML przy użyciu `Imports` instrukcja jest taki sam jak składni używanej w kodzie XML. W związku z tym można skopiować deklaracja przestrzeni nazw z pliku XML i użyć go w `Imports` instrukcji.  
  
 Prefiksy przestrzeni nazw XML są przydatne, gdy chcesz utworzyć wielokrotnie elementów XML, które pochodzą z tego samego obszaru nazw. Prefiks przestrzeni nazw XML zadeklarowana z `Imports` instrukcji jest globalna w tym sensie, że jest dostępna dla całego kodu w pliku. Można go użyć podczas tworzenia literały — element XML i jeśli dostęp do właściwości osi XML. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) i [właściwości osi XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).  
  
 Jeśli zdefiniujesz globalnej przestrzeni nazw XML bez prefiksu przestrzeni nazw (na przykład `Imports <xmlns="http://SomeNameSpace>"`), tej przestrzeni nazw jest traktowane jako domyślna przestrzeń nazw XML. Domyślny obszar nazw XML jest używany dla literałów XML elementu lub właściwości osi atrybutu XML, które nie określają jawnie przestrzeni nazw. Domyślnej przestrzeni nazw jest również używana, gdy określonego obszaru nazw jest pusta przestrzeń nazw (czyli `xmlns=""`). Domyślna przestrzeń nazw XML nie ma zastosowania do atrybutów XML w literałach XML lub właściwości osi atrybutu XML, które nie mają przestrzeni nazw.  
  
 Przestrzenie nazw XML zdefiniowanego w pliku XML literału, które są nazywane *lokalnej przestrzeni nazw XML*, pierwszeństwo przestrzeni nazw XML, które są zdefiniowane przez `Imports` instrukcji jako globalnego. Przestrzenie nazw XML, które są definiowane przez `Imports` instrukcji mają pierwszeństwo przed zaimportowane dla projektu Visual Basic przestrzeni nazw XML. Jeśli literał XML definiuje obszar nazw XML, tym lokalną przestrzeń nazw nie ma zastosowania do wyrażenia osadzone.  
  
 Globalne przestrzenie nazw XML zgodne z definicji i określania zakresu regułami jako przestrzenie nazw .NET Framework. W związku z tym można uwzględnić `Imports` instrukcji, aby zdefiniować globalnej przestrzeni nazw XML dowolnym można zaimportować obszaru nazw .NET Framework. Obejmuje to zarówno pliki kodu i importowane przestrzenie nazw poziom projektu. Informacje o poziomie projektu importowanych przestrzeni nazw, zobacz [strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
 Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcje. Te muszą być zgodne deklaracje opcji, takich jak `Option Strict` instrukcji i musi poprzedzać deklaracji elementu programowania, takich jak `Module` lub `Class` instrukcje.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład importuje domyślnej przestrzeni nazw XML i oznaczone symbolem prefiks przestrzeni nazw XML `ns`. Następnie tworzy literałów XML, które używają obu tych przestrzeni nazw.  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład importuje prefiks przestrzeni nazw XML `ns`. Tworzy literał XML używa prefiksu przestrzeni nazw, który wyświetla formularz końcowego elementu.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Zwróć uwagę, kompilator przekonwertować prefiks przestrzeni nazw XML z globalnego prefiksu do definicji lokalnego prefiks.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład importuje prefiks przestrzeni nazw XML `ns`. Następnie używa prefiks przestrzeni nazw do utworzenia literału XML i dostępu do pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Zobacz też  
 [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [GetXmlNamespace — Operator](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
