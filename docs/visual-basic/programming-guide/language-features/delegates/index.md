---
title: Delegaty (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fe21d8c0dcefaea35d9f96cd2ecbff92a1c83d36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="delegates-visual-basic"></a>Delegaty (Visual Basic)
Obiekty delegowane są obiekty, które odwołują się do metody. One nazywane *wskaźników funkcji bezpieczny* ponieważ są one podobne do wskaźników funkcji używane w innych językach programowania. Jednak w przeciwieństwie do wskaźników funkcji [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] obiektów delegowanych jest typem referencyjnym, oparty na klasie <xref:System.Delegate?displayProperty=nameWithType>. Delegatów mogą odwoływać się obu metod udostępnionych — metody, które można wywołać bez określonego wystąpienia klasy — wystąpienie metody.  
  
## <a name="delegates-and-events"></a>Delegaci i zdarzenia  
 Obiekty delegowane są przydatne w sytuacjach konieczne pośredniczący między wywołanie procedury i procedury wywoływanej. Na przykład może być obiekt, który informuje o zdarzeniach, aby można było wywołać programów obsługi zdarzeń w różnych okolicznościach. Niestety obiekt wywoływanie zdarzeń nie może znać wcześniejsze obsługi zdarzeń, które obsługuje określone zdarzenie. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Umożliwia obsługę zdarzeń dynamicznie Powiąż ze zdarzeniami, tworząc delegowanego dla Ciebie, korzystając z `AddHandler` instrukcji. W czasie wykonywania delegat przekazuje wywołań obsługi zdarzeń odpowiednie.  
  
 Chociaż można tworzyć własne delegatów w większości przypadków [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tworzy delegata i zajmuje się szczegóły dla Ciebie. Na przykład `Event` instrukcji niejawnie definiuje klasę delegata o nazwie `<EventName>EventHandler` jako klasa zagnieżdżona zawierających klasy `Event` instrukcji i z takiego samego podpisu jak zdarzenia. `AddressOf` Instrukcja niejawnie tworzy wystąpienia delegata, który odwołuje się do określonej procedury. Następujące dwa wiersze kodu są równoważne. W pierwszym wierszu, zobacz jawne utworzenie wystąpienia `Eventhandler`, z odwołaniem do metody `Button1_Click` wysyłane jako argument. Drugi wiersz jest wygodny sposób, aby zrobić to samo.  
  
 [!code-vb[VbVbalrDelegates#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_1.vb)]  
  
 Można użyć skrótu sposobem tworzenia delegatów w dowolnym miejscu kompilator może ustalić typu delegata w kontekście.  
  
## <a name="declaring-events-that-use-an-existing-delegate-type"></a>Typ delegata zdarzenia deklarujący Użyj istniejącego  
 W niektórych sytuacjach można zadeklarować zdarzenia, aby użyć istniejącego typu delegata jako jego podstawowy delegata. Następującej składni pokazano, jak:  
  
 [!code-vb[VbVbalrDelegates#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_2.vb)]  
  
 Jest to przydatne, gdy chcesz rozesłać wiele zdarzeń do tej procedury obsługi.  
  
## <a name="delegate-variables-and-parameters"></a>Parametry i zmienne delegata  
 Można używać delegatów dla innych, niż zdarzenie powiązane zadania, takie jak wolnych wątków lub za pomocą procedur, które należy wywołać różne wersje funkcji w czasie wykonywania.  
  
 Załóżmy na przykład, aplikacja sklasyfikowane ad, która zawiera pola listy z nazwami samochodów. Reklam są sortowane według tytułu, który jest zwykle markę samochód. Problem, które mogą się spodziewać występuje, gdy niektóre samochodów obejmują roku samochodu przed markę. Problem jest, że funkcje wbudowane sortowania pola listy sortuje tylko przez kody znaków; umieszcza wszystkie reklam, począwszy od daty najpierw, a następnie reklam, począwszy od marki.  
  
 Aby rozwiązać ten problem, można utworzyć procedury sortowania w klasie, która używa standardowych sortowania alfabetycznego na większości pola listy, ale może przełączyć się w czasie wykonywania procedury sortowania niestandardowego samochodu reklam. Aby to zrobić, należy przekazać procedury sortowania niestandardowego do klasy sortowania w czasie wykonywania, używanie delegatów.  
  
## <a name="addressof-and-lambda-expressions"></a>AddressOf i wyrażenia Lambda  
 Każda klasa delegata definiuje konstruktora, który jest przekazywany specyfikację metody obiektu. Argument do konstruktora delegata musi być odwołaniem do metody lub wyrażenia lambda.  
  
 Aby określić odwołań do metody, należy użyć następującej składni:  
  
 `AddressOf` [`expression`.]`methodName`  
  
 Typ kompilacji `expression` musi być nazwą klasy lub interfejsu, który zawiera metodę o określonej nazwie, w których Podpis pasuje do podpisu klasie obiektów delegowanych. `methodName` Może być udostępnionej metody lub metodą wystąpienia. `methodName` Nie jest opcjonalny, nawet w przypadku utworzenia delegata dla metody domyślnej klasy.  
  
 Aby określić wyrażenie lambda, użyj następującej składni:  
  
 `Function`([`parm` Jako `type`, `parm2` jako `type2`,...])`expression`  
  
 W poniższym przykładzie przedstawiono oba `AddressOf` i wyrażenia lambda, można określić odwołania do delegata.  
  
 [!code-vb[VbVbalrDelegates#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_3.vb)]  
  
 Podpis funkcji musi być zgodny z typem obiektu delegowanego. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md). Aby uzyskać więcej przykładów wyrażenia lambda i `AddressOf` przypisania do delegatów, zobacz [swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: wywoływanie metody delegata](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|Przykład pokazujący sposób skojarzyć metodę z delegata, a następnie wywołać tej metody za pomocą obiektu delegowanego.|  
|[Porady: przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|Pokazuje, jak używać delegatów do przekazania jednej procedury do innej procedury.|  
|[Swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|W tym artykule opisano, jak można przypisać typu Sub i funkcji do delegatów lub obsługi nawet wtedy, gdy ich podpisów nie są identyczne|  
|[Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)|Zawiera omówienie zdarzeń w języku Visual Basic.|
