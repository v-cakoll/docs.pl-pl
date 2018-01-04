---
title: "Instrukcje: Wdrażanie asynchronicznej operacji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 276dd3cc84c15c66adeab30f86583e6d9eec4144
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Instrukcje: Wdrażanie asynchronicznej operacji usługi
W [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji, operacja usługi można zaimplementować asynchronicznie lub synchronicznie bez dyktowanie do klienta, jak wywołać ją. Na przykład można można synchronicznie wywoływania operacji asynchronicznych usługi i operacji synchronicznych usługi może być wywołana asynchronicznie. Na przykład pokazujący sposób asynchroniczne wywoływanie operacji w aplikacji klienta, zobacz [porady: wywołania operacji usługi asynchronicznie](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]operacje synchroniczne i asynchroniczne, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md) i [synchroniczne i asynchroniczne operacje](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md). W tym temacie opisano podstawową strukturę asynchronicznej operacji usługi, kodu nie została ukończona. Pełny przykład stron usługa i klient zobacz [asynchronicznym](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Implementuje operację usługi asynchronicznie  
  
1.  W umowy serwisowej należy zadeklarować pary metod asynchronicznych zgodnie z wytycznymi projektowania asynchroniczne .NET. `Begin` Metoda przyjmuje parametr obiektu wywołania zwrotnego i obiektu stanu i zwraca <xref:System.IAsyncResult?displayProperty=nameWithType> i odpowiadający mu `End` metody pobierającej <xref:System.IAsyncResult?displayProperty=nameWithType> i zwraca wartość zwracaną. Aby uzyskać więcej informacji dotyczących wywołań asynchronicznych, zobacz [asynchroniczne wzorce projektowe programowania](http://go.microsoft.com/fwlink/?LinkId=248221).  
  
2.  Oznacz `Begin` metody pary metod asynchronicznych z <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atrybutu i ustaw <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> właściwości `true`. Na przykład następujący kod wykonuje kroki 1 i 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  Implementowanie `Begin/End` pary metod w klasie usługi, zgodnie z wytycznymi projektowania asynchronicznego. Na przykład poniższy przykładowy kod przedstawia implementację, w którym napisano ciąg do konsoli w obu `Begin` i `End` części asynchronicznej operacji usługi, a wartość zwracaną `End` operacji zwracana do klienta. Na przykład kompletny kod zobacz sekcję przykład.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach kodu pokazano:  
  
1.  Interfejsu kontraktu usługi z:  
  
    1.  Synchronicznego `SampleMethod` operacji.  
  
    2.  Asynchroniczne `BeginSampleMethod` operacji.  
  
    3.  Asynchroniczne `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` pary operacji.  
  
2.  Implementacja usługi przy użyciu <xref:System.IAsyncResult?displayProperty=nameWithType> obiektu.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Operacje synchroniczne i asynchroniczne](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
