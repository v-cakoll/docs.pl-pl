---
title: Interfejsy magazynu symboli diagnostycznych
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 34eee8c05e1c356d4c431245c6837bd2b3a89b32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504475"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="14a8f-102">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="14a8f-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="14a8f-103">W tym temacie opisano niezarządzane interfejsy, które umożliwiają kompilatorowi generowanie informacji o symbolach do użycia przez debuger.</span><span class="sxs-lookup"><span data-stu-id="14a8f-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14a8f-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="14a8f-104">In This Section</span></span>  
 [<span data-ttu-id="14a8f-105">IBindingDisplay — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-105">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="14a8f-106">Dostarcza metody, które wyświetlają bieżące informacje o powiązaniu dla działającej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="14a8f-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="14a8f-107">IDebugAutoAttach — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-107">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="14a8f-108">Definiuje interfejs dla automatycznie dołączanego debugera dla serwera.</span><span class="sxs-lookup"><span data-stu-id="14a8f-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="14a8f-109">INotifyConnection2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-109">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="14a8f-110">Deklaruje metody rejestrowania źródła powiadomień połączenia i wyrejestrowywania go.</span><span class="sxs-lookup"><span data-stu-id="14a8f-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="14a8f-111">INotifySink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-111">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="14a8f-112">Deklaruje metody powiadamiania o ujściach.</span><span class="sxs-lookup"><span data-stu-id="14a8f-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="14a8f-113">INotifySource2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="14a8f-114">Deklaruje metodę ustawiania filtrów powiadomień.</span><span class="sxs-lookup"><span data-stu-id="14a8f-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="14a8f-115">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="14a8f-116">Zawiera informacje dotyczące funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="14a8f-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="14a8f-117">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-117">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="14a8f-118">Ten interfejs jest uzupełnieniem odczytu do [interfejsu ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="14a8f-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="14a8f-119">ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="14a8f-120">Zezwala na definiowanie opcjonalnych informacji o metodzie asynchronicznej dla symbolu metody.</span><span class="sxs-lookup"><span data-stu-id="14a8f-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="14a8f-121">Musi być używana z otwartą metodą (czyli między wywołaniami [metody OpenMethod —](isymunmanagedwriter-openmethod-method.md)i [CloseMethod —](isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="14a8f-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="14a8f-122">ISymUnmanagedBinder — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-122">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="14a8f-123">Reprezentuje spinacz symboliczny dla niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="14a8f-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="14a8f-124">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-124">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="14a8f-125">Reprezentuje segregator symboliczny dla kodu niezarządzanego i rozszerza `ISymUnmanagedBinder` interfejs.</span><span class="sxs-lookup"><span data-stu-id="14a8f-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="14a8f-126">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-126">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="14a8f-127">Reprezentuje segregator symboliczny dla kodu niezarządzanego i rozszerza `ISymUnmanagedBinder` interfejs.</span><span class="sxs-lookup"><span data-stu-id="14a8f-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="14a8f-128">ISymUnmanagedConstant — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-128">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="14a8f-129">Zapewnia dostęp do stałych niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="14a8f-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="14a8f-130">ISymUnmanagedDispose — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-130">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="14a8f-131">Usuwa niezarządzane zasoby.</span><span class="sxs-lookup"><span data-stu-id="14a8f-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="14a8f-132">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-132">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="14a8f-133">Reprezentuje dokument, do którego odwołuje się magazyn symboli.</span><span class="sxs-lookup"><span data-stu-id="14a8f-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="14a8f-134">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-134">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="14a8f-135">Zapewnia metody zapisu do dokumentu, do którego odwołuje się magazyn symboli.</span><span class="sxs-lookup"><span data-stu-id="14a8f-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="14a8f-136">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-136">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="14a8f-137">Zapewnia metody funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="14a8f-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="14a8f-138">ISymUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-138">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="14a8f-139">Reprezentuje metodę w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="14a8f-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="14a8f-140">ISymUnmanagedNamespace, interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-140">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="14a8f-141">Reprezentuje przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="14a8f-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="14a8f-142">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-142">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="14a8f-143">Reprezentuje czytnik symboli, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="14a8f-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="14a8f-144">ISymUnmanagedReader2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-144">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="14a8f-145">Pobiera metodę czytnika symboli, używając tokenu metody oraz numeru wersji Edit-and-Copy.</span><span class="sxs-lookup"><span data-stu-id="14a8f-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="14a8f-146">ISymUnmanagedReaderSymbolSearchInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="14a8f-147">Dostarcza metody, które pobierają informacje o wyszukiwaniu symboli.</span><span class="sxs-lookup"><span data-stu-id="14a8f-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="14a8f-148">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-148">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="14a8f-149">Reprezentuje zakres leksykalny w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="14a8f-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="14a8f-150">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-150">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="14a8f-151">Reprezentuje zakres leksykalny w ramach metody i rozszerza `ISymUnmanagedScope` interfejs przy użyciu metod, które pobierają informacje o stałych zdefiniowanych w zakresie.</span><span class="sxs-lookup"><span data-stu-id="14a8f-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="14a8f-152">ISymUnmanagedSourceServerModule — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-152">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="14a8f-153">Zapewnia dane serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="14a8f-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="14a8f-154">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="14a8f-155">Dostarcza metody, które pobierają informacje o ścieżce wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="14a8f-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="14a8f-156">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-156">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="14a8f-157">Reprezentuje zmienną, taką jak parametr, zmienna lokalna lub pole.</span><span class="sxs-lookup"><span data-stu-id="14a8f-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="14a8f-158">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-158">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="14a8f-159">Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="14a8f-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="14a8f-160">ISymUnmanagedWriter2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-160">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="14a8f-161">Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="14a8f-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="14a8f-162">Rozszerza `ISymUnmanagedWriter` interfejs.</span><span class="sxs-lookup"><span data-stu-id="14a8f-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="14a8f-163">ISymUnmanagedWriter3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-163">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="14a8f-164">Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="14a8f-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="14a8f-165">Rozszerza `ISymUnmanagedWriter` interfejs.</span><span class="sxs-lookup"><span data-stu-id="14a8f-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="14a8f-166">ISymUnmanagedWriter4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-166">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="14a8f-167">Interfejs ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="14a8f-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="14a8f-168">ISymUnmanagedWriter5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14a8f-168">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="14a8f-169">Interfejs ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="14a8f-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="14a8f-170">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="14a8f-170">Related Sections</span></span>  
 [<span data-ttu-id="14a8f-171">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="14a8f-171">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="14a8f-172">Struktury magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="14a8f-172">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="14a8f-173">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="14a8f-173">Debugging</span></span>](../debugging/index.md)
