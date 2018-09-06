---
title: Imports, instrukcja - Namespace XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 1100afd89b27e789c0db713291ed3656092fb0c7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802395"
---
# <a name="imports-statement-xml-namespace"></a>Imports — Instrukcja (przestrzeń nazw XML)
Importuje prefiksy przestrzeni nazw XML do użycia w literałach XML i właściwości osi XML.  
  
## <a name="syntax"></a>Składnia  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>Części  
 `xmlNamespacePrefix`  
 Opcjonalna. Ciąg, który XML elementy i atrybuty mogą odwoływać się do `xmlNamespaceName`. Jeśli nie `xmlNamespacePrefix` jest podany, importowanych przestrzeni nazw XML jest domyślny obszar nazw XML. Musi być prawidłowym identyfikatorem XML. Aby uzyskać więcej informacji, zobacz [nazwy z zadeklarowane elementy i atrybuty XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  
  
 `xmlNamespaceName`  
 Wymagane. Ciąg identyfikujący importowanych przestrzeni nazw XML.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `Imports` instrukcji, aby zdefiniować globalnej przestrzeni nazw XML, korzystających z literały XML i właściwości osi XML lub przekazywane jako parametry do `GetXmlNamespace` operatora. (Aby uzyskać informacje o używaniu `Imports` instrukcję, aby zaimportować alias, który może służyć użycia nazwy typów w kodzie, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Składnia deklaracji przestrzeni nazw XML przy użyciu `Imports` instrukcja jest taka sama jak składnią używaną w formacie XML. W związku z tym, możesz skopiować deklarację przestrzeni nazw z pliku XML i korzystać z niej w `Imports` instrukcji.  
  
 Prefiksy przestrzeni nazw XML są przydatne, jeśli chcesz regularnie tworzyć elementy XML, które pochodzą z tej samej przestrzeni nazw. Prefiks przestrzeni nazw XML zadeklarowane za pomocą `Imports` instrukcja jest globalne w tym sensie, że jest ona dostępna dla całego kodu w pliku. Można użyć go po utworzeniu literały — element XML i jeśli uzyskujesz dostęp do właściwości osi XML. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) i [właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md).  
  
 Jeśli zdefiniujesz globalnej przestrzeni nazw XML bez prefiksu przestrzeni nazw (na przykład `Imports <xmlns="http://SomeNameSpace>"`), przestrzeń nazw jest traktowane jako domyślny obszar nazw XML. Domyślny obszar nazw XML jest używany dla literałów — element XML i właściwości osi atrybutu XML, które nie są określone jawnie przestrzeni nazw. Domyślny obszar nazw jest również używana, gdy określonego obszaru nazw jest pusta przestrzeń nazw (czyli `xmlns=""`). Domyślny obszar nazw XML nie ma zastosowania do atrybutów XML w literałach XML lub do właściwości osi atrybutu XML, które nie mają przestrzeni nazw.  
  
 Obszary nazw XML, które są zdefiniowane w pliku XML literału, są one nazywane *lokalne obszary nazw XML*, pierwszeństwo przestrzeni nazw XML, które są zdefiniowane przez `Imports` instrukcję jako globalne. Przestrzenie nazw XML, które są definiowane przez `Imports` instrukcji mają pierwszeństwo przed przestrzeni nazw XML zaimportowane dla projektów języka Visual Basic. Jeśli literał XML definiuje obszar nazw XML, że lokalną przestrzeń nazw nie ma zastosowania do wyrażenia osadzone.  
  
 Globalnej przestrzeni nazw XML, wykonaj te same reguły zakresu i definicji jako przestrzeni nazw .NET Framework. W rezultacie mogą obejmować `Imports` instrukcji, aby zdefiniować globalnej przestrzeni nazw XML dowolnym miejscu importujesz przestrzeń nazw .NET Framework. Obejmuje to zarówno pliki kodu, jak i na poziomie projektu importowanych przestrzeni nazw. Aby uzyskać informacji na temat importowanych przestrzeni nazw na poziomie projektu, zobacz [strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
 Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcji. Te należy wykonać, opcja deklaracji, takich jak `Option Strict` instrukcji, dlatego musi poprzedzać deklaracji elementu programowania, takich jak `Module` lub `Class` instrukcji.  
  
## <a name="example"></a>Przykład  
 Następujący przykład importuje, domyślnej przestrzeni nazw XML i zidentyfikowanego za prefiks przestrzeni nazw XML `ns`. Następnie tworzy ona literałach XML, które używają obu tych przestrzeni nazw.  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a>Przykład  
 Następujący przykład importuje prefiks przestrzeni nazw XML `ns`. Następnie tworzy literał XML używa prefiksu przestrzeni nazw, która wyświetla formularz końcowego elementu.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Zwróć uwagę, kompilator przekonwertować prefiks przestrzeni nazw XML z globalnego prefiksu, do definicji lokalnego prefiks.  
  
## <a name="example"></a>Przykład  
 Następujący przykład importuje prefiks przestrzeni nazw XML `ns`. Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostępem pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Zobacz też  
 [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md)  
 [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [GetXmlNamespace, operator](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
