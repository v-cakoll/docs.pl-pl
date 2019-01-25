---
title: 'Instrukcje: Określ, której członkami są sprawdzane pod kątem konfliktów współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: 1007cbc0961d01574fd60ec50eb63406ec7adef9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724583"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="a19c6-102">Instrukcje: Określ, której członkami są sprawdzane pod kątem konfliktów współbieżności</span><span class="sxs-lookup"><span data-stu-id="a19c6-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>
<span data-ttu-id="a19c6-103">Zastosuj jedną z trzech typów wyliczeniowych do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić, które elementy członkowskie, które mają być uwzględniane w ramach aktualizacji sprawdza, czy wykrywanie konfliktów optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="a19c6-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="a19c6-104"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (Mapowane w czasie projektowania) jest używana w połączeniu z funkcjami współbieżności środowiska wykonawczego w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a19c6-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="a19c6-105">Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a19c6-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a19c6-106">Oryginalne wartości elementów członkowskich są porównywane z bieżącym stanem bazy danych, tak długo, jak żadnego elementu członkowskiego jest wyznaczony jako `IsVersion=true`.</span><span class="sxs-lookup"><span data-stu-id="a19c6-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="a19c6-107">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="a19c6-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="a19c6-108">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="a19c6-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="a19c6-109">Aby zawsze używać tego elementu członkowskiego do wykrywania konfliktów</span><span class="sxs-lookup"><span data-stu-id="a19c6-109">To always use this member for detecting conflicts</span></span>  
  
1.  <span data-ttu-id="a19c6-110">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a19c6-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="a19c6-111">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartość właściwości `Always`.</span><span class="sxs-lookup"><span data-stu-id="a19c6-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="a19c6-112">Aby nigdy nie używaj tego elementu członkowskiego do wykrywania konfliktów</span><span class="sxs-lookup"><span data-stu-id="a19c6-112">To never use this member for detecting conflicts</span></span>  
  
1.  <span data-ttu-id="a19c6-113">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a19c6-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="a19c6-114">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartość właściwości `Never`.</span><span class="sxs-lookup"><span data-stu-id="a19c6-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="a19c6-115">Do użycia tego elementu członkowskiego na potrzeby wykrywania konfliktów, tylko wtedy, gdy aplikacja została zmieniona wartość elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="a19c6-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1.  <span data-ttu-id="a19c6-116">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a19c6-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="a19c6-117">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartość właściwości `WhenChanged`.</span><span class="sxs-lookup"><span data-stu-id="a19c6-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a19c6-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="a19c6-118">Example</span></span>  
 <span data-ttu-id="a19c6-119">Poniższy przykład określa, że `HomePage` obiektów nigdy nie powinny być badane podczas sprawdzania aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="a19c6-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="a19c6-120">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="a19c6-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a19c6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a19c6-121">See also</span></span>
- [<span data-ttu-id="a19c6-122">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="a19c6-122">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="a19c6-123">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="a19c6-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
