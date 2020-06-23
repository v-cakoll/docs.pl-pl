---
title: 'Instrukcje: Wdrażanie asynchronicznej operacji usługi'
description: Dowiedz się więcej na temat struktury operacji usługi asynchronicznej w obszarze WFC. Operacja usługi może być implementowana asynchronicznie lub synchronicznie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 5f890bd5124e2353cecee37d163b7f2c65b87fde
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244624"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Instrukcje: Wdrażanie asynchronicznej operacji usługi
W aplikacjach Windows Communication Foundation (WCF) operacja usługi może być implementowana asynchronicznie lub synchronicznie bez konieczności podania klientowi metody wywołania. Na przykład asynchroniczne operacje usługi mogą być wywoływane synchronicznie, a operacje usług synchronicznych można wywołać asynchronicznie. Przykład pokazujący sposób wywołania operacji asynchronicznie w aplikacji klienckiej można znaleźć w temacie [How to: Call operacje usługi asynchronicznie](./feature-details/how-to-call-wcf-service-operations-asynchronously.md). Aby uzyskać więcej informacji na temat operacji synchronicznych i asynchronicznych, zobacz [Projektowanie kontraktów usług](designing-service-contracts.md) i [operacji synchronicznych i asynchronicznych](synchronous-and-asynchronous-operations.md). W tym temacie opisano podstawową strukturę asynchronicznej operacji usługi, kod nie został ukończony. Pełny przykład obu stron usługi i klienta można znaleźć w temacie [asynchronicznie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Zaimplementuj asynchroniczną operację usługi  
  
1. W kontrakcie usługi Zadeklaruj parę metod asynchronicznych zgodnie z wytycznymi dotyczącymi asynchronicznego projektowania platformy .NET. `Begin`Metoda przyjmuje parametr, obiekt wywołania zwrotnego i obiekt stanu, a następnie zwraca <xref:System.IAsyncResult?displayProperty=nameWithType> metodę zgodną, `End` która pobiera <xref:System.IAsyncResult?displayProperty=nameWithType> i zwraca wartość zwracaną. Aby uzyskać więcej informacji o wywołaniach asynchronicznych, zobacz [asynchroniczne programowanie wzorów wzorców](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
2. Oznacz `Begin` metodę pary metod asynchronicznych <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atrybutem i ustaw <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> Właściwość na `true` . Na przykład poniższy kod wykonuje kroki 1 i 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. Zaimplementuj `Begin/End` parę metod w klasie usługi zgodnie z wytycznymi dotyczącymi projektowania asynchronicznego. Na przykład poniższy kod ilustruje implementację, w której ciąg jest zapisywana w konsoli programu `Begin` i `End` części operacji usługi asynchronicznej, a zwracana wartość `End` operacji jest zwracana do klienta. Aby zapoznać się z kompletnym przykładem kodu, zapoznaj się z sekcją przykładową.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykłady kodu:  
  
1. Interfejs kontraktu usługi z:  
  
    1. Operacja synchroniczna `SampleMethod` .  
  
    2. Operacja asynchroniczna `BeginSampleMethod` .  
  
    3. `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` Para operacji asynchronicznych.  
  
2. Implementacja usługi przy użyciu <xref:System.IAsyncResult?displayProperty=nameWithType> obiektu.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Projektowanie kontraktów usług](designing-service-contracts.md)
- [Operacje synchroniczne i asynchroniczne](synchronous-and-asynchronous-operations.md)
