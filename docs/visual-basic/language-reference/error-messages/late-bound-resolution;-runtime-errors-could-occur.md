---
title: Rozpoznanie późnego wiązania; mogą wystąpić błędy podczas wykonywania
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: af027b7752fdf13f1540010a8ddb681182c1b23c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588782"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="20fa6-102">Rozpoznanie późnego wiązania; mogą wystąpić błędy podczas wykonywania</span><span class="sxs-lookup"><span data-stu-id="20fa6-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="20fa6-103">Obiekt jest przypisany do zmiennej zadeklarowany za [Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="20fa6-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="20fa6-104">Gdy zadeklarować zmiennej jako `Object`, należy wykonać kompilator *późne wiązanie*, co powoduje, że dodatkowe operacje w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="20fa6-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="20fa6-105">Prezentuje ona potencjalne błędy czasu wykonywania przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="20fa6-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="20fa6-106">Na przykład w przypadku przypisania <xref:System.Windows.Forms.Form> do `Object` zmiennej, a następnie spróbuj uzyskać dostępu do <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> zgłasza wyjątek środowiska uruchomieniowego, właściwości, <xref:System.MemberAccessException> ponieważ <xref:System.Windows.Forms.Form> klasy nie ujawnia `NameTable` właściwości.</span><span class="sxs-lookup"><span data-stu-id="20fa6-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="20fa6-107">Jeśli należy zadeklarować zmienną określonego typu, kompilator może wykonywać *wczesne wiązanie* w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="20fa6-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="20fa6-108">Powoduje to lepszą wydajność, kontroli dostępu do elementów członkowskich z określonego typu i zwiększenia czytelności kodu.</span><span class="sxs-lookup"><span data-stu-id="20fa6-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="20fa6-109">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="20fa6-109">By default, this message is a warning.</span></span> <span data-ttu-id="20fa6-110">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="20fa6-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="20fa6-111">**Identyfikator błędu:** BC42017</span><span class="sxs-lookup"><span data-stu-id="20fa6-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="20fa6-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="20fa6-112">To correct this error</span></span>  
  
-   <span data-ttu-id="20fa6-113">Jeśli to możliwe należy zadeklarować zmienną określonego typu.</span><span class="sxs-lookup"><span data-stu-id="20fa6-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20fa6-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20fa6-114">See Also</span></span>  
 [<span data-ttu-id="20fa6-115">Wczesne i późne powiązania</span><span class="sxs-lookup"><span data-stu-id="20fa6-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="20fa6-116">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="20fa6-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
