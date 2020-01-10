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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708878"
---
# <a name="how-to-create-user-defined-exceptions"></a>Jak utworzyć wyjątki zdefiniowane przez użytkownika

.NET dostarcza hierarchię klas wyjątków wywodzących się z klasy podstawowej <xref:System.Exception>. Jeśli żaden z wstępnie zdefiniowanych wyjątków nie spełnia Twoich potrzeb, możesz utworzyć własne klasy wyjątków wywodzące się z klasy <xref:System.Exception>.

Podczas tworzenia własnych wyjątków, należy zakończyć nazwę klasy wyjątku zdefiniowanego przez użytkownika z wyrazem "Exception" i zaimplementować trzy typowe konstruktory, jak pokazano w poniższym przykładzie. W przykładzie zdefiniowano nową klasę wyjątku o nazwie `EmployeeListNotFoundException`. Klasa pochodzi od <xref:System.Exception> i zawiera trzy konstruktory.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> Jeśli używasz komunikacji zdalnej, upewnij się, że metadane zdefiniowane przez użytkownika wyjątków są dostępne na serwerze (strona wywoływana) i dla klienta (obiekt serwera proxy lub strona wywołująca). Aby dowiedzieć się więcej, zobacz [Najlepsze praktyki dotyczące wyjątków](best-practices-for-exceptions.md).

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
