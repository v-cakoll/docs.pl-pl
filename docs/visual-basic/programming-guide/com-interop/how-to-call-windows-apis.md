---
title: 'Porady: wywoływanie Windows API (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 081f4242ef5883a8b25b8819ba3aff835b1e6ac7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208273"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Porady: wywoływanie Windows API (Visual Basic)
W tym przykładzie definiuje i wywołuje `MessageBox` funkcji w bibliotece user32.dll i następnie przekazuje ciąg do niego.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System> przestrzeni nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Metoda nie jest statyczna, jest abstrakcyjny lub został wcześniej zdefiniowany. Typ elementu nadrzędnego jest interfejsem lub długość *nazwa* lub *Nazwa_pliku_dll* wynosi zero. (<xref:System.ArgumentException>)  
  
-   *Nazwa* lub *Nazwa_pliku_dll* jest `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   Typ zawierający poprzednio utworzono za pomocą `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Zobacz także

- [Im bliżej wywołania platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
- [Przykłady wywołań platformy](../../../framework/interop/platform-invoke-examples.md)  
- [Wykorzystywanie niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
- [Definiowanie metody przy użyciu odbicia emisji](https://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
- [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
