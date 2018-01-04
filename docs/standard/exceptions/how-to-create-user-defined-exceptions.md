---
title: "Porady: tworzenie wyjątków zdefiniowanych przez użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c55489a4c0b86142fcda99c5962c896b73691cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
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
