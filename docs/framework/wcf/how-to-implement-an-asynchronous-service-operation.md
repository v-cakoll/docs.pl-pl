---
title: 'Instrukcje: Wdrażanie asynchronicznej operacji usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: eeea3933446a401ad8f556dc546f54122a19a8b5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723889"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Instrukcje: Wdrażanie asynchronicznej operacji usługi
W aplikacjach Windows Communication Foundation (WCF) Operacja usługi może być implementowany asynchronicznego lub synchronicznego bez dyktowanie do klienta, jak wywołać go. Na przykład operacje asynchroniczne usługi można wywoływać synchronicznie, a operacje synchroniczne usługi, które mogą być wywoływane asynchronicznie. Na przykład, który pokazuje, jak asynchroniczne wywoływanie operacji w aplikacji klienckiej, zobacz [porady: wywoływanie operacji usługi asynchronicznie](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Aby uzyskać więcej informacji na temat operacje synchroniczne i asynchroniczne, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md) i [synchroniczne i asynchroniczne operacje](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md). W tym temacie opisano podstawowe struktury asynchronicznej operacji usługi, gdy kod nie jest gotowy. Pełny przykład stron usługi i klienta, zobacz [asynchroniczne](https://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Operacje synchroniczne i asynchroniczne](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
