---
title: Rozpoznanie późnego wiązania; mogą wystąpić błędy podczas wykonywania
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: f1dc656a09eee05080356892b280a79505f3b9cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397353"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="933f4-102">Rozpoznanie późnego wiązania; mogą wystąpić błędy podczas wykonywania</span><span class="sxs-lookup"><span data-stu-id="933f4-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="933f4-103">Obiekt jest przypisany do zmiennej zadeklarowanej jako [Typ danych obiektu](../data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="933f4-103">An object is assigned to a variable declared to be of the [Object Data Type](../data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="933f4-104">Po zadeklarowaniu zmiennej jako `Object` , kompilator musi wykonać *późne wiązanie*, co powoduje dodatkowe operacje w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="933f4-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="933f4-105">Udostępnia również aplikacji potencjalne błędy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="933f4-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="933f4-106">Na przykład, Jeśli przypiszesz <xref:System.Windows.Forms.Form> do `Object` zmiennej, a następnie spróbujesz uzyskać dostęp do <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> właściwości, środowisko uruchomieniowe zgłosi, <xref:System.MemberAccessException> ponieważ Klasa nie <xref:System.Windows.Forms.Form> uwidacznia `NameTable` właściwości.</span><span class="sxs-lookup"><span data-stu-id="933f4-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="933f4-107">W przypadku deklarowania zmiennej jako określonego typu kompilator może wykonać *wczesne powiązanie* w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="933f4-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="933f4-108">Powoduje to zwiększenie wydajności, kontrolowany dostęp do elementów członkowskich określonego typu i lepszą czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="933f4-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="933f4-109">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="933f4-109">By default, this message is a warning.</span></span> <span data-ttu-id="933f4-110">Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="933f4-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="933f4-111">**Identyfikator błędu:** BC42017</span><span class="sxs-lookup"><span data-stu-id="933f4-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="933f4-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="933f4-112">To correct this error</span></span>  
  
- <span data-ttu-id="933f4-113">Jeśli to możliwe, zadeklaruj zmienną jako określonego typu.</span><span class="sxs-lookup"><span data-stu-id="933f4-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933f4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="933f4-114">See also</span></span>

- [<span data-ttu-id="933f4-115">Wczesne i późne powiązania</span><span class="sxs-lookup"><span data-stu-id="933f4-115">Early and Late Binding</span></span>](../../programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="933f4-116">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="933f4-116">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
