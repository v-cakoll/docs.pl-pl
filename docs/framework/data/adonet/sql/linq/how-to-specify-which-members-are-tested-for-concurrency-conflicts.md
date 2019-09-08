---
title: 'Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: de7109e0fed0eb7c1975ad7360a7588ef9b294ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793141"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="51735-102">Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności</span><span class="sxs-lookup"><span data-stu-id="51735-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>
<span data-ttu-id="51735-103">Zastosuj jeden z trzech typów wyliczeniowych [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] do <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić, które składowe mają być uwzględnione w testach aktualizacji w celu wykrywania optymistycznych konfliktów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="51735-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="51735-104">Właściwość (zamapowana w czasie projektowania) jest używana razem z funkcjami współbieżności w czasie wykonywania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]w systemie. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A></span><span class="sxs-lookup"><span data-stu-id="51735-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="51735-105">Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="51735-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51735-106">Pierwotne wartości elementów członkowskich są porównywane z bieżącym stanem bazy danych, o ile nie `IsVersion=true`wyznaczono żadnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="51735-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="51735-107">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="51735-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="51735-108">Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="51735-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="51735-109">Aby zawsze używać tego elementu członkowskiego do wykrywania konfliktów</span><span class="sxs-lookup"><span data-stu-id="51735-109">To always use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="51735-110"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="51735-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="51735-111">`Always`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości na.</span><span class="sxs-lookup"><span data-stu-id="51735-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="51735-112">Aby nigdy nie używać tego elementu członkowskiego do wykrywania konfliktów</span><span class="sxs-lookup"><span data-stu-id="51735-112">To never use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="51735-113"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="51735-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="51735-114">`Never`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości na.</span><span class="sxs-lookup"><span data-stu-id="51735-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="51735-115">Aby użyć tego elementu członkowskiego do wykrywania konfliktów tylko wtedy, gdy aplikacja zmieniła wartość elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="51735-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1. <span data-ttu-id="51735-116"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="51735-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="51735-117">`WhenChanged`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości na.</span><span class="sxs-lookup"><span data-stu-id="51735-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51735-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="51735-118">Example</span></span>  
 <span data-ttu-id="51735-119">W poniższym przykładzie określono, `HomePage` że obiekty nigdy nie powinny być testowane podczas sprawdzania aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="51735-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="51735-120">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="51735-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="51735-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51735-121">See also</span></span>

- [<span data-ttu-id="51735-122">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="51735-122">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="51735-123">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="51735-123">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
