---
title: Praca z obiektami dynamicznymi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 14bd78f2897edc9f2092e062fda16ba5a7d04c37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640865"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Praca z obiektami dynamicznymi (Visual Basic)
Obiektów dynamicznych to kolejny sposób, w innych niż `Object` typ późne powiązania do obiektu w czasie wykonywania. Obiekt dynamiczny udostępnia składowych, takich jak właściwości i metody w czasie wykonywania przy użyciu dynamicznych interfejsów, które są zdefiniowane w <xref:System.Dynamic> przestrzeni nazw. Można użyć klas w <xref:System.Dynamic> przestrzeni nazw do tworzenia obiektów, które działają z struktur danych, które nie są zgodne, typu statycznego lub w formacie. Można również użyć obiektów dynamicznych, które są zdefiniowane w dynamicznych języków, takich jak IronPython i IronRuby. Przykłady pokazujące, jak utworzyć obiekty dynamiczne lub użyć obiekt dynamiczny, zdefiniowane w języka dynamicznego, zobacz [instruktażu: Tworzenie obiektów dynamicznych i posługiwanie](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, lub <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic wiąże obiektów z środowisko uruchomieniowe języka dynamicznego i języki dynamiczne, takie jak IronPython i IronRuby przy użyciu <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejsu. Przykłady klas, które implementują `IDynamicMetaObjectProvider` interfejsu są <xref:System.Dynamic.DynamicObject> i <xref:System.Dynamic.ExpandoObject> klasy.  
  
 Jeśli wykonano wywołanie z późnym wiązaniem do obiektu, który implementuje `IDynamicMetaObjectProvider` interfejsu powiązań języka Visual Basic do obiekt dynamiczny za pomocą tego interfejsu. Jeśli wykonano wywołanie z późnym wiązaniem do obiektu, który nie implementuje `IDynamicMetaObjectProvider` interfejsu, lub jeśli wywołanie `IDynamicMetaObjectProvider` interfejsu zakończy się niepowodzeniem, Visual Basic wiąże obiekt przy użyciu możliwości późne powiązania w czasie wykonywania w języku Visual Basic.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [Przewodnik: Tworzenie obiektów dynamicznych i posługiwanie](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
