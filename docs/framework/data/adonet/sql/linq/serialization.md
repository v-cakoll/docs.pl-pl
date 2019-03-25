---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: 56ebe888b816972f8d72873e4fca9f5204e6c772
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408928"
---
# <a name="serialization"></a>Serializacja
W tym temacie opisano [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] możliwości serializacji. Sekcjach poniżej zawierają informacje dotyczące sposobu dodawania serializacji podczas generowania kodu w czasie projektowania i zachowania czasu wykonywania serializacji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] klasy.  
  
 Możesz dodać kod serializacji w czasie projektowania, przy użyciu jednej z następujących metod:  
  
-   W [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], zmień **tryb serializacji** właściwości **Unidirectional**.  
  
-   W wierszu polecenia SQLMetal Dodaj **/serialization** opcji. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Omówienie  
 Kod wygenerowany przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślnie udostępnia funkcje odroczonego ładowania. Odroczone ładowanie jest bardzo wygodne w warstwie pośredniej przezroczysty podczas ładowania danych na żądanie. Jednak jest kłopotliwy dla serializacji, ponieważ element serializujący wyzwala odroczonego ładowania, czy odroczonego ładowania jest przeznaczone. W efekcie gdy obiekt jest serializowana, jego zamknięcia przechodnie w obszarze wszystkie odwołania wychodzące Odrocz załadowanych jest serializowana.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Funkcji serializacji rozwiązuje ten problem, głównie za pośrednictwem dwóch mechanizmów:  
  
-   A <xref:System.Data.Linq.DataContext> tryb wyłączanie odroczonego ładowania (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>). Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.DataContext>.  
  
-   Przełącznik generowania kodu, aby wygenerować <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> i <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atrybuty w wygenerowanym jednostek. Ten aspekt zachowanie odroczone ładowanie klas w obszarze serializacji, w tym podlega głównych części tego tematu.  
  
### <a name="definitions"></a>Definicje  
  
-   *Serializator DataContract*: Domyślny element serializujący używany przez składnik usług Windows Communication Framework (WCF) programu .NET Framework 3.0 lub nowszej wersji.  
  
-   *Serializacja jednokierunkowe*: Wersja serializacji klasę, która zawiera tylko właściwość jednokierunkowe skojarzenia (w celu uniknięcia cyklu). Zgodnie z Konwencją właściwość po stronie nadrzędnej relacji klucza obcego podstawowy jest oznaczony do serializacji. Druga strona skojarzenia dwukierunkowe nie jest serializowana.  
  
     Jednokierunkowe serializacji jest jedynym typem serializacji obsługiwane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="code-example"></a>Przykład kodu  
 W poniższym kodzie użyto tradycyjne `Customer` i `Order` klasy z przykładowej bazy danych Northwind i pokazuje, jak te klasy są oznaczone za pomocą atrybutów serializacji.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 Dla `Order` klasy w poniższym przykładzie, tylko do właściwości skojarzenia odwrotnej odpowiadający `Customer` klasy jest wyświetlany w celu skrócenia programu. Nie ma <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu, aby uniknąć cyklu.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>Jak do serializacji jednostek  
 Może wykonywać serializację jednostek w kodzie, pokazana w poprzedniej sekcji;  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>Relacje cykliczne samodzielnie  
 Relacje cykliczne Self postępuj zgodnie z tym samym wzorcem. Właściwość skojarzenia odpowiadający klucza obcego nie ma <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu właściwość nadrzędna nie.  
  
 Należy wziąć pod uwagę następujące klasy, która ma dwie relacje cykliczne samoobsługowego: Employee.Manager/Reports i Employee.Mentor/Mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Zobacz także
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Instrukcje: Umożliwianie serializacji jednostek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)
