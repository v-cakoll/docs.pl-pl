---
title: Procedury składowane CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: c02efa3f0a91d176b626761335bd2d5a2b96b966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917960"
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
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
