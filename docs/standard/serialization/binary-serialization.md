---
title: Serializacja binarna
description: W tym artykule opisano serializację i typy binarne, dla których obsługuje platformę .NET Core. Należy pamiętać o zagrożeniu serializacji binarnej i alternatywom.
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: c735d30920fd3c8cd13243b4a5a29489ce05b262
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289697"
---
# <a name="binary-serialization"></a><span data-ttu-id="0ab7a-104">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="0ab7a-104">Binary serialization</span></span>

<span data-ttu-id="0ab7a-105">Serializacja mogą być definiowane jako proces przechowywania stanu obiektu na nośniku.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-105">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="0ab7a-106">W trakcie tego procesu publiczny i prywatny pola obiektu oraz nazwę klasy, łącznie z zestawu zawierającego klasy, są konwertowane na strumień bajtów, które są następnie zapisywane do strumienia danych.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-106">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="0ab7a-107">Gdy obiekt jest następnie przeprowadzona, dokładną oryginalnego obiektu zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-107">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="0ab7a-108">W przypadku implementowania mechanizmu serializacji w środowisku zorientowanym obiektowo trzeba zwiększyć liczbę kompromisów między łatwośćmi użytkowania i elastyczność.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-108">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="0ab7a-109">Ten proces można automatycznego w dużym stopniu, pod warunkiem, że podane są wystarczające kontrolę nad procesem.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-109">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="0ab7a-110">Mogą na przykład wystąpić sytuacje, w których prosta Serializacja binarna nie jest wystarczająca lub może istnieć specyficzny powód, aby określić, które pola w klasie muszą być serializowane.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-110">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="0ab7a-111">W poniższych sekcjach opisano niezawodny mechanizm serializacji zapewniany z platformą .NET oraz kilka ważnych funkcji, które umożliwiają dostosowanie procesu do własnych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-111">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="0ab7a-112">Stan UTF-8 lub UTF-7 kodowany obiektu nie jest zachowana, jeśli obiekt jest serializacji i deserializacji za pomocą różnych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-112">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="0ab7a-113">Serializacja binarna pozwala modyfikować prywatne elementy członkowskie wewnątrz obiektu i w związku z tym zmieniać jego stan.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-113">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="0ab7a-114">Z tego względu zalecane są inne platformy serializacji, takie jak <xref:System.Text.Json?displayProperty=fullName> , które działają na publicznej powierzchni interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-114">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="0ab7a-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="0ab7a-115">.NET Core</span></span>

<span data-ttu-id="0ab7a-116">Platforma .NET Core obsługuje serializację binarne dla podzbioru typów.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-116">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="0ab7a-117">Listę obsługiwanych typów można zobaczyć w poniższej sekcji [typy serializowane](#serializable-types) .</span><span class="sxs-lookup"><span data-stu-id="0ab7a-117">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="0ab7a-118">Wymienione typy są gwarantowane do serializacji między .NET Framework 4.5.1 i nowszymi wersjami oraz między programem .NET Core 2,0 i jego nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-118">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="0ab7a-119">Inne implementacje platformy .NET, takie jak mono, nie są oficjalnie obsługiwane, ale również powinny funkcjonować.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-119">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="0ab7a-120">Typy możliwe do serializacji</span><span class="sxs-lookup"><span data-stu-id="0ab7a-120">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="0ab7a-121">Typ</span><span class="sxs-lookup"><span data-stu-id="0ab7a-121">Type</span></span> | <span data-ttu-id="0ab7a-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ab7a-122">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-123">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-124">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-125">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-126">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-127">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-128">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-129">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-130">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-131">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-132">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-133">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-134">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-134">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-135">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-136">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-136">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="0ab7a-137">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-138">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-139">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-140">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-140">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-141">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-141">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-142">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-142">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="0ab7a-143">Serializacja z .NET Framework do platformy .NET Core nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-143">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-144">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-145">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-146">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-147">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-148">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-149">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-150">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-151">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-151">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-152">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-153">Począwszy od platformy .NET Core 2.0.2 i nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-153">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-154">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-155">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-156">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-156">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-157">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-158">Jeśli ustawisz `RemotingFormat` wartość `SerializationFormat.Binary` , może ona być wymieniana tylko z platformą .net Core 2,1 i nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-158">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-159">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-160">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-161">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-162">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-163">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-164">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-165">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-166">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-167">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-168">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-169">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-169">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-170">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-170">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-171">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-171">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="0ab7a-172">Serializacja z .NET Framework do platformy .NET Core nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="0ab7a-172">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-173">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-174">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-175">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-176">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-177">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-178">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-179">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-180">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-181">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="0ab7a-182">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-183">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-184">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-185">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-186">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-187">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-188">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-189">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-190">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-191">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-192">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-193">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-194">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-195">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-196">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-197">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-198">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-199">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-200">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-201">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-202">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-203">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-204">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-205">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-206">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-206">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-207">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-208">Począwszy od platformy .NET Core 2.0.6.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-208">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-209">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-210">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-211">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-212">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="0ab7a-213">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-214">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-215">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-216">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-217">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-218">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-219">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-220">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-221">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-222">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-223">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-224">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-225">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-226">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-227">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-228">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-229">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-230">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-231">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-232">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-233">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-234">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-235">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-236">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-237">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-238">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-239">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-240">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-241">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-242">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-243">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-244">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-245">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-246">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-247">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-248">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-249">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-250">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-251">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-252">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-253">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-254">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-255">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-256">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-257">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-258">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-259">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-259">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-260">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-260">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-261">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-261">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="0ab7a-262">Serializacja z .NET Framework do platformy .NET Core nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-262">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-263">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-264">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-265">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-266">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-267">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-268">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-269">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-270">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-271">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-272">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-273">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-274">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-275">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-276">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-277">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-278">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-279">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-280">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-281">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-281">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-282">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-283">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-283">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="0ab7a-284">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-285">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-286">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-286">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-287">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-287">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-288">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-288">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="0ab7a-289">Ograniczone dane serializacji.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-289">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-290">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-291">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-292">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-293">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-294">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-295">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-296">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-297">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-298">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-299">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-300">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-301">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-302">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-303">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-304">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-305">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-306">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-307">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-308">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-309">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-310">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-311">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-312">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-313">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-314">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-315">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-316">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-317">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-318">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-319">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-320">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-321">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-321">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-322">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-323">Nie można serializować w .NET Framework 4,7 i wcześniejszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-323">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-324">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-325">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-326">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-327">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-328">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-328">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-329">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-329">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="0ab7a-330">Począwszy od platformy .NET Core 2.0.4.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-330">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0ab7a-331">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ab7a-331">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="0ab7a-332">Zawiera klasy, które mogą być używane do serializacji i deserializacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-332">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="0ab7a-333">[Serializacja XML i SOAP](xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="0ab7a-333">[XML and SOAP Serialization](xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="0ab7a-334">Opisuje mechanizm serializacji XML, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-334">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="0ab7a-335">[Zabezpieczenia i Serializacja](../../framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="0ab7a-335">[Security and Serialization](../../framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="0ab7a-336">Opisuje bezpiecznego wskazówek kodowania, które należy wykonać podczas pisania kodu, który będzie wykonywać serializacji.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-336">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="0ab7a-337">[Komunikacja zdalna .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0ab7a-337">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="0ab7a-338">Opisuje różne metody, które są uruchamiane w .NET Framework na potrzeby komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-338">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="0ab7a-339">[Usługi sieci Web XML utworzone za pomocą ASP.NET i klientów usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0ab7a-339">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="0ab7a-340">Artykuły opisujące i objaśniające sposób programowania usług sieci Web XML utworzonych za pomocą ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0ab7a-340">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
