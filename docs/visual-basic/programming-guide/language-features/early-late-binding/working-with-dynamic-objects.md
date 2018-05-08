---
title: Praca z obiektami dynamicznymi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 78b17a379ea219cc24842322703caaa9d29eeb2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Praca z obiektami dynamicznymi (Visual Basic)
Obiekty dynamiczne Podaj inny sposób inny niż `Object` typ późne wiązanie z obiektu w czasie wykonywania. Obiekt dynamiczny uwidacznia elementy członkowskie, takie jak właściwości i metody w czasie wykonywania za pomocą dynamicznej interfejsów, które są zdefiniowane w <xref:System.Dynamic> przestrzeni nazw. Można użyć klasy w <xref:System.Dynamic> przestrzeni nazw do tworzenia obiektów, które współpracują z struktury danych, które nie są zgodne, statyczne typ lub format. Umożliwia także obiekty dynamiczne, które są zdefiniowane w dynamicznej języków, takich jak IronPython i IronRuby. Przykłady, które pokazują, jak utworzyć obiekty dynamiczne lub użyć obiekt dynamiczny zdefiniowany w języku dynamicznej, zobacz [wskazówki: tworzenie i użycie obiekty dynamiczne](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, lub <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic wiąże obiektów ze środowiska uruchomieniowego języka dynamicznego i dynamiczne języków, takich jak IronPython i IronRuby przy użyciu <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejsu. Przykłady klas implementujących `IDynamicMetaObjectProvider` interfejsu są <xref:System.Dynamic.DynamicObject> i <xref:System.Dynamic.ExpandoObject> klasy.  
  
 Jeśli wywołanie późnym wiązaniem dotyczące obiekt, który implementuje `IDynamicMetaObjectProvider` interfejsu powiązania przy użyciu języka Visual Basic do dynamicznego obiektu przy użyciu tego interfejsu. Jeśli wykonano wywołanie z późnym wiązaniem do obiektu, który nie implementuje `IDynamicMetaObjectProvider` interfejsu, lub jeśli wywołanie `IDynamicMetaObjectProvider` interfejsu nie powiedzie się, Visual Basic wiąże obiekt przy użyciu możliwości późne wiązanie środowiska uruchomieniowego języka Visual Basic.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
