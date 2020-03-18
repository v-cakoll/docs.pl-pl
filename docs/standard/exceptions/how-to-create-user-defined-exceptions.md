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
ms.openlocfilehash: 6de00490a17fff005dd50a7acc5247089c073f68
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708878"
---
# <a name="how-to-create-user-defined-exceptions"></a>Jak utworzyć wyjątki zdefiniowane przez użytkownika

.NET udostępnia hierarchię klas wyjątków ostatecznie pochodzących <xref:System.Exception>z klasy podstawowej . Jednak jeśli żaden ze wstępnie zdefiniowanych wyjątków spełnia twoje potrzeby, można utworzyć <xref:System.Exception> własne klasy wyjątków, wywodząc się z klasy.

Podczas tworzenia własnych wyjątków, zakończyć nazwę klasy wyjątku zdefiniowane przez użytkownika ze słowem "Wyjątek" i zaimplementować trzy typowe konstruktory, jak pokazano w poniższym przykładzie. Przykład definiuje nową klasę wyjątku o nazwie `EmployeeListNotFoundException`. Klasa pochodzi od <xref:System.Exception> i zawiera trzy konstruktory.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> W sytuacjach, gdy używasz komunikacji zdalnej, należy upewnić się, że metadane dla wyjątków zdefiniowanych przez użytkownika jest dostępna na serwerze (wywoływany) i klienta (obiekt proxy lub obiekt wywołujący). Aby uzyskać więcej informacji, zobacz [Najważniejsze wskazówki dotyczące wyjątków](best-practices-for-exceptions.md).

## <a name="see-also"></a>Zobacz też

- [Wyjątki](index.md)
