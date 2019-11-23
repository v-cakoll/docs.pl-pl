---
title: 'Instrukcje: Wdrażanie asynchronicznej operacji usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: b706ec49db123f33b3fc1ab0f420ed9a47e32f67
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320953"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Instrukcje: Wdrażanie asynchronicznej operacji usługi
W aplikacjach Windows Communication Foundation (WCF) operacja usługi może być implementowana asynchronicznie lub synchronicznie bez konieczności podania klientowi metody wywołania. Na przykład asynchroniczne operacje usługi mogą być wywoływane synchronicznie, a operacje usług synchronicznych można wywołać asynchronicznie. Przykład pokazujący sposób wywołania operacji asynchronicznie w aplikacji klienckiej można znaleźć w temacie [How to: Call operacje usługi asynchronicznie](./feature-details/how-to-call-wcf-service-operations-asynchronously.md). Aby uzyskać więcej informacji na temat operacji synchronicznych i asynchronicznych, zobacz [Projektowanie kontraktów usług](designing-service-contracts.md) i [operacji synchronicznych i asynchronicznych](synchronous-and-asynchronous-operations.md). W tym temacie opisano podstawową strukturę asynchronicznej operacji usługi, kod nie został ukończony. Pełny przykład obu stron usługi i klienta można znaleźć w temacie [asynchronicznie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Zaimplementuj asynchroniczną operację usługi  
  
1. W kontrakcie usługi Zadeklaruj parę metod asynchronicznych zgodnie z wytycznymi dotyczącymi asynchronicznego projektowania platformy .NET. Metoda `Begin` przyjmuje parametr, obiekt wywołania zwrotnego i obiekt stanu, a następnie zwraca <xref:System.IAsyncResult?displayProperty=nameWithType> i pasującą metodę `End`, która przyjmuje <xref:System.IAsyncResult?displayProperty=nameWithType> i zwraca wartość zwracaną. Aby uzyskać więcej informacji o wywołaniach asynchronicznych, zobacz [asynchroniczne programowanie wzorów wzorców](https://go.microsoft.com/fwlink/?LinkId=248221).  
  
2. Oznacz metodę `Begin` pary metod asynchronicznych atrybutem <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> i ustaw właściwość <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> na `true`. Na przykład poniższy kod wykonuje kroki 1 i 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. Zaimplementuj parę metod `Begin/End` w klasie usługi zgodnie z wytycznymi dotyczącymi projektowania asynchronicznego. Na przykład poniższy kod ilustruje implementację, w której ciąg jest zapisywana w konsoli programu zarówno `Begin`, jak i `End` części operacji usługi asynchronicznej, a zwracana wartość operacji `End` jest zwracana do klienta. Aby zapoznać się z kompletnym przykładem kodu, zapoznaj się z sekcją przykładową.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykłady kodu:  
  
1. Interfejs kontraktu usługi z:  
  
    1. Synchroniczna operacja `SampleMethod`.  
  
    2. Asynchroniczna operacja `BeginSampleMethod`.  
  
    3. Para operacji `EndServiceAsyncMethod` asynchronicznych /`BeginServiceAsyncMethod`.  
  
2. Implementacja usługi przy użyciu obiektu <xref:System.IAsyncResult?displayProperty=nameWithType>.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Projektowanie kontraktów usług](designing-service-contracts.md)
- [Operacje synchroniczne i asynchroniczne](synchronous-and-asynchronous-operations.md)
