---
title: Praca z obiektami dynamicznymi
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 20d007fb48e1db352bab6d8e25d2e60e02554732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345167"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Praca z obiektami dynamicznymi (Visual Basic)
Obiekty dynamiczne zapewniają inny sposób, inny niż typ `Object`, do późnego powiązania z obiektem w czasie wykonywania. Obiekt dynamiczny ujawnia składowe, takie jak właściwości i metody w czasie wykonywania, przy użyciu interfejsów dynamicznych, które są zdefiniowane w przestrzeni nazw <xref:System.Dynamic>. Klas w przestrzeni nazw <xref:System.Dynamic> można użyć do tworzenia obiektów, które współpracują ze strukturami danych, które nie pasują do typu statycznego lub formatu. Można również używać obiektów dynamicznych, które są zdefiniowane w językach dynamicznych, takich jak IronPython i IronRuby. Przykłady pokazujące sposób tworzenia obiektów dynamicznych lub korzystania z obiektu dynamicznego zdefiniowanego w języku dynamicznym można znaleźć w temacie [Przewodnik: Tworzenie i używanie obiektów dynamicznych](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>lub <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic powiązania z obiektami z poziomu środowiska uruchomieniowego języka dynamicznego i języków dynamicznych, takich jak IronPython i IronRuby, przy użyciu interfejsu <xref:System.Dynamic.IDynamicMetaObjectProvider>. Przykłady klas implementujących interfejs `IDynamicMetaObjectProvider` są klasami <xref:System.Dynamic.DynamicObject> i <xref:System.Dynamic.ExpandoObject>.  
  
 W przypadku wywołania z późnym wiązaniem do obiektu, który implementuje interfejs `IDynamicMetaObjectProvider`, Visual Basic tworzy powiązanie z obiektem dynamicznym przy użyciu tego interfejsu. W przypadku wywołania z późnym wiązaniem do obiektu, który nie implementuje interfejsu `IDynamicMetaObjectProvider` lub jeśli wywołanie interfejsu `IDynamicMetaObjectProvider` kończy się niepowodzeniem, Visual Basic powiązać z obiektem przy użyciu możliwości późnego wiązania środowiska uruchomieniowego Visual Basic.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [Przewodnik: Tworzenie obiektów dynamicznych i korzystanie z nich](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
