---
title: 'Porady: tworzenie wyjątków zdefiniowanych przez użytkownika'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90bf9d6dbfebf8f7c1aa22e5844cf4e30b89b8d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-user-defined-exceptions"></a>Tworzenie wyjątków zdefiniowanych przez użytkownika

.NET zawiera hierarchię ostatecznie pochodzi od klasy podstawowej klasy wyjątków <xref:System.Exception>. Jednak jeśli żadna z wstępnie zdefiniowane wyjątki nie spełnia Twoje potrzeby, można utworzyć własne klasy wyjątku przez pochodny <xref:System.Exception> klasy.

Podczas tworzenia własnych wyjątki, kończyć nazwę klasy wyjątków zdefiniowanych przez użytkownika od słowa "Wyjątku", a wdrożenie trzy konstruktorów wspólne, jak pokazano w poniższym przykładzie. W przykładzie zdefiniowano klasę wyjątku o nazwie `EmployeeListNotFoundException`. Klasa pochodzi od <xref:System.Exception> i zawiera trzy konstruktorów.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> W sytuacjach, gdy używasz usług zdalnych należy się upewnić, że metadane wyjątki zdefiniowane przez użytkownika jest dostępny na serwerze (wywoływany) i klienta (obiekt serwera proxy lub wywołujący). Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące wyjątków](best-practices-for-exceptions.md).

## <a name="see-also"></a>Zobacz też  
[Wyjątki](index.md)
