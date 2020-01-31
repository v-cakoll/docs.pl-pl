---
title: Współdziałanie wyjątków
ms.date: 01/16/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 2aff71e97e1be0dbb584f4fe43c322cea86d2480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795176"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>Praca z wyjątkami międzyoperacyjnymi w kodzie niezarządzanym

Międzyoperacyjność wyjątku kodu niezarządzanego jest obsługiwana tylko na platformach systemu Windows. Problemy z przenośnością powstają na platformach innych niż Windows. Ponieważ ABI systemu UNIX nie ma definicji obsługi wyjątków, kod zarządzany nie może wiedzieć, jak mechanizmy wyjątków działają w ramach okładek. W związku z tym wyjątki mogą kończyć się wynikiem nieprzewidywalnych zachowań i awarii.

## <a name="setjmplongjmp-behaviors"></a>Zachowania setjmp/longjmp

Współdziałanie z funkcjami `setjmp` i `longjmp` języka C nie jest obsługiwane. Nie można użyć `longjmp`, aby pominąć ramki zarządzane.

Aby uzyskać więcej informacji, zobacz [dokumentację longjmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
- [Współdziałanie z natywnymi bibliotekami](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
