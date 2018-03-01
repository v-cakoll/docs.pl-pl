---
title: Praca z obiektami dynamicznymi (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da70c1e4c7398ad46d48c85b62ab884675bd1a73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Praca z obiektami dynamicznymi (Visual Basic)
Obiekty dynamiczne Podaj inny sposób inny niż `Object` typ późne wiązanie z obiektu w czasie wykonywania. Obiekt dynamiczny uwidacznia elementy członkowskie, takie jak właściwości i metody w czasie wykonywania za pomocą dynamicznej interfejsów, które są zdefiniowane w <xref:System.Dynamic> przestrzeni nazw. Można użyć klasy w <xref:System.Dynamic> przestrzeni nazw do tworzenia obiektów, które współpracują z struktury danych, które nie są zgodne, statyczne typ lub format. Umożliwia także obiekty dynamiczne, które są zdefiniowane w dynamicznej języków, takich jak IronPython i IronRuby. Przykłady, które pokazują, jak utworzyć obiekty dynamiczne lub użyć obiekt dynamiczny zdefiniowany w języku dynamicznej, zobacz [wskazówki: tworzenie i użycie obiekty dynamiczne](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, lub <xref:System.Dynamic.ExpandoObject>.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]wiąże obiektów ze środowiska uruchomieniowego języka dynamicznego i dynamiczne języków, takich jak IronPython i IronRuby przy użyciu <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejsu. Przykłady klas implementujących `IDynamicMetaObjectProvider` interfejsu są <xref:System.Dynamic.DynamicObject> i <xref:System.Dynamic.ExpandoObject> klasy.  
  
 Jeśli wywołanie późnym wiązaniem dotyczące obiekt, który implementuje `IDynamicMetaObjectProvider` interfejsu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wiąże obiekt dynamiczny przy użyciu tego interfejsu. Jeśli wykonano wywołanie z późnym wiązaniem do obiektu, który nie implementuje `IDynamicMetaObjectProvider` interfejsu, lub, jeśli wywołanie `IDynamicMetaObjectProvider` interfejsu kończy się niepowodzeniem, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wiąże obiekt przy użyciu możliwości późne wiązanie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] środowiska wykonawczego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
