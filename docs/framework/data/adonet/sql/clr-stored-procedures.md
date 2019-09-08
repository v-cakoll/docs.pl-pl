---
title: Procedury składowane CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: d2fde4fdcd5ab63906256d814256578b9baa9ecd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782501"
---
# <a name="clr-stored-procedures"></a>Procedury składowane CLR
Procedury składowane są procedurami, których nie można używać w wyrażeniach skalarnych. Mogą zwracać wyniki tabelaryczne i komunikaty do klienta, wywoływać instrukcje języka definicji danych (DDL) i języka manipulowania danymi oraz zwracać parametry wyjściowe.  
  
> [!NOTE]
> Firma Microsoft Visual Basic nie obsługuje parametrów wyjściowych w taki sam sposób, jak C# w przypadku programu Microsoft Visual. Należy określić, aby przekazać parametr przez odwołanie i zastosować \<atrybut out () > do reprezentowania parametru wyjściowego, tak jak w poniższym:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Aby uzyskać szczegółowe informacje, zobacz wersję [dokumentacji SQL Server](/sql) dla używanej wersji SQL Server.
  
 **Dokumentacja SQL Server**

1. [Procedury składowane CLR](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie obiektów SQL Server 2005 w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [Omówienie ADO.NET](../ado-net-overview.md)
