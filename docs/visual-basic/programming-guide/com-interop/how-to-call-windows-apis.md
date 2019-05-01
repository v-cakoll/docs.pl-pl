---
title: 'Instrukcje: Wywoływanie Windows API (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: e7b76495b83cb9a1dfe7629a1d82695d2046eac2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61818719"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Instrukcje: Wywoływanie Windows API (Visual Basic)
W tym przykładzie definiuje i wywołuje `MessageBox` funkcji w bibliotece user32.dll i następnie przekazuje ciąg do niego.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołanie do <xref:System> przestrzeni nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Metoda nie jest statyczna, jest abstrakcyjny lub został wcześniej zdefiniowany. Typ elementu nadrzędnego jest interfejsem lub długość *nazwa* lub *Nazwa_pliku_dll* wynosi zero. (<xref:System.ArgumentException>)  
  
- *Nazwa* lub *Nazwa_pliku_dll* jest `Nothing`. (<xref:System.ArgumentNullException>)  
  
- Typ zawierający poprzednio utworzono za pomocą `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Zobacz także

- [Im bliżej wywołania platformy](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Przykłady wywołań platformy](../../../framework/interop/platform-invoke-examples.md)
- [Wykorzystywanie niezarządzanych funkcji DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Definiowanie metody przy użyciu odbicia emisji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
