---
title: 'Instrukcje: Wdrażanie asynchronicznej operacji usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 00cbea3ae4528016a736c639c07059c1d2cb6407
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332042"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Instrukcje: Wdrażanie asynchronicznej operacji usługi
W aplikacjach Windows Communication Foundation (WCF) Operacja usługi może być implementowany asynchronicznego lub synchronicznego bez dyktowanie do klienta, jak wywołać go. Na przykład operacje asynchroniczne usługi można wywoływać synchronicznie, a operacje synchroniczne usługi, które mogą być wywoływane asynchronicznie. Na przykład, który pokazuje, jak asynchroniczne wywoływanie operacji w aplikacji klienckiej, zobacz [jak: Asynchroniczne wywoływanie operacji usługi](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Aby uzyskać więcej informacji na temat operacje synchroniczne i asynchroniczne, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md) i [synchroniczne i asynchroniczne operacje](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md). W tym temacie opisano podstawowe struktury asynchronicznej operacji usługi, gdy kod nie jest gotowy. Aby uzyskać pełny przykład stron usługi i klienta, zobacz [asynchroniczne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Asynchroniczne wykonania operacji usługi  
  
1.  W Twojej umowy serwisowej zadeklarować pary metod asynchronicznych, zgodnie z wytycznymi projektowania asynchronicznego .NET. `Begin` Metoda przyjmuje parametr, obiektu wywołania zwrotnego i obiektu stanu i zwraca <xref:System.IAsyncResult?displayProperty=nameWithType> i pasującą `End` metody, która przyjmuje <xref:System.IAsyncResult?displayProperty=nameWithType> i zwraca wartość zwracaną. Aby uzyskać więcej informacji na temat wywołania asynchroniczne, zobacz [Asynchronous Programming Patterns projektowania](https://go.microsoft.com/fwlink/?LinkId=248221).  
  
2.  Oznacz `Begin` metoda pary metod asynchronicznych za pomocą <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atrybut i ustawić <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> właściwość `true`. Na przykład poniższy kod wykonuje kroki 1 i 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  Implementowanie `Begin/End` pary metod w klasie usługi zgodnie z wytycznymi projektowania asynchronicznego. Na przykład poniższy kod pokazuje implementację, w którym ciąg jest zapisywany do konsoli w obu `Begin` i `End` fragmenty asynchronicznej operacji usługi i wartość zwracana przez `End` operacji zwracana do klienta. W przykładzie kompletny kod znajduje się w sekcji przykład.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach kodu pokazano:  
  
1.  Przy użyciu interfejsu kontraktu usługi:  
  
    1.  Synchroniczne `SampleMethod` operacji.  
  
    2.  Asynchroniczna `BeginSampleMethod` operacji.  
  
    3.  Asynchroniczna `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` pary operacji.  
  
2.  Implementacja usługi przy użyciu <xref:System.IAsyncResult?displayProperty=nameWithType> obiektu.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- [Projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md)
- [Operacje synchroniczne i asynchroniczne](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
