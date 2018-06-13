---
title: 'Porady: wywoływanie Windows API (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: de568c3273d4d040c6566136e5d59e2155b86f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643643"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Porady: wywoływanie Windows API (Visual Basic)
W tym przykładzie definiuje i wywołuje `MessageBox` funkcji w user32.dll, a następnie przekazuje ciąg do niego.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System> przestrzeni nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Metoda nie jest statyczny, jest abstrakcyjna lub został wcześniej zdefiniowany. Typ nadrzędny jest interfejsem lub długość *nazwa* lub *dllName* wynosi zero. (<xref:System.ArgumentException>)  
  
-   *Nazwa* lub *dllName* jest `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   Typ zawierający wcześniej utworzono za pomocą `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Zobacz też  
 [Bliższe spojrzenie na platformie wywołania](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [Przykłady wywołań platformy](../../../framework/interop/platform-invoke-examples.md)  
 [Wykorzystywanie niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [Emituj definiowanie metody za pomocą odbicia](http://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
