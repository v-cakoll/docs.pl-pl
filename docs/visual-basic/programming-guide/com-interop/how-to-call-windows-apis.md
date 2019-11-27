---
title: 'Porady: wywoływanie Windows API'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 6f3c53243d7aeb73be81796d5ca185c3a3c41c72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348702"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Porady: wywoływanie Windows API (Visual Basic)
Ten przykład definiuje i wywołuje funkcję `MessageBox` w User32. dll, a następnie przekazuje do niej ciąg.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołanie do przestrzeni nazw <xref:System>.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Metoda nie jest statyczna, jest abstrakcyjna lub została wcześniej zdefiniowana. Typ nadrzędny jest interfejsem lub długość *nazwy* lub *nazwa_pliku_dll* ma wartość zero. (<xref:System.ArgumentException>)  
  
- *Nazwa* lub *nazwa_pliku_dll* jest `Nothing`. (<xref:System.ArgumentNullException>)  
  
- Typ zawierający został wcześniej utworzony przy użyciu `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Zobacz także

- [Bliższe spojrzenie na wywołanie platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Przykłady wywołań platformy](../../../framework/interop/platform-invoke-examples.md)
- [Wykorzystywanie niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Definiowanie metody przy użyciu emisji odbicia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
