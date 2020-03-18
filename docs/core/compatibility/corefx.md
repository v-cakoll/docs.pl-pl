---
title: Zmiany podziału biblioteki klas podstawowych
description: Wyświetla listę zmian w .NET CoreFx, bibliotece klas podstawowych.
ms.date: 09/20/2019
ms.openlocfilehash: 56a3cf4f4c00a79752d5a98bb086bb9f8c0614b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147578"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="e0d6d-103">Przełomowe zmiany w CoreFx</span><span class="sxs-lookup"><span data-stu-id="e0d6d-103">CoreFx breaking changes</span></span>

<span data-ttu-id="e0d6d-104">CoreFx zapewnia elementy podstawowe i inne typy ogólne używane przez .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0d6d-104">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="e0d6d-105">Na tej stronie udokumentowane są następujące zmiany dotyczące zasad:</span><span class="sxs-lookup"><span data-stu-id="e0d6d-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="e0d6d-106">Przełomowa zmiana</span><span class="sxs-lookup"><span data-stu-id="e0d6d-106">Breaking change</span></span> | <span data-ttu-id="e0d6d-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e0d6d-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="e0d6d-108">Interfejsy API, które zgłaszają wersję raportu teraz zgłosić produkt, a nie wersji pliku</span><span class="sxs-lookup"><span data-stu-id="e0d6d-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="e0d6d-109">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-109">3.0</span></span> |
| [<span data-ttu-id="e0d6d-110">Niestandardowe wystąpienia Buforu ConerFallbackBuffer nie mogą wycofać się cyklicznie</span><span class="sxs-lookup"><span data-stu-id="e0d6d-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="e0d6d-111">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-111">3.0</span></span> |
| [<span data-ttu-id="e0d6d-112">Zmiany zachowania formatowania i analizowania zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="e0d6d-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="e0d6d-113">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-113">3.0</span></span> |
| [<span data-ttu-id="e0d6d-114">Operacje analizy zmiennoprzecinkowych nie są już inwakczliwe ani nie mogą być powodem do przepełnieniaWyjątek</span><span class="sxs-lookup"><span data-stu-id="e0d6d-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="e0d6d-115">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-115">3.0</span></span> |
| [<span data-ttu-id="e0d6d-116">InvalidAsynchronousStateException przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="e0d6d-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="e0d6d-117">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-117">3.0</span></span> |
| [<span data-ttu-id="e0d6d-118">NET Core 3.0 następuje unicode najlepszych rozwiązań podczas zastępowania nieprawidłowo sformułowane sekwencje bajtów UTF-8</span><span class="sxs-lookup"><span data-stu-id="e0d6d-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="e0d6d-119">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-119">3.0</span></span> |
| [<span data-ttu-id="e0d6d-120">Atrybut TypeDescriptionProviderAttribute przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="e0d6d-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="e0d6d-121">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-121">3.0</span></span> |
| [<span data-ttu-id="e0d6d-122">ZipArchiveEntry nie obsługuje już archiwów z niespójnymi rozmiarami wejść</span><span class="sxs-lookup"><span data-stu-id="e0d6d-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="e0d6d-123">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-123">3.0</span></span> |
| [<span data-ttu-id="e0d6d-124">JSON serializator typ wyjątku zmieniono z JsonException do NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="e0d6d-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="e0d6d-125">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-125">3.0</span></span> |
| [<span data-ttu-id="e0d6d-126">Zmiana semantyki (ciągu)null w Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="e0d6d-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="e0d6d-127">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-127">3.0</span></span> |
| [<span data-ttu-id="e0d6d-128">JsonEncodedText.Encode metody mają dodatkowy argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="e0d6d-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="e0d6d-129">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-129">3.0</span></span> |
| [<span data-ttu-id="e0d6d-130">Zmieniono podpis JsonFactoryConverter.CreateConverter</span><span class="sxs-lookup"><span data-stu-id="e0d6d-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="e0d6d-131">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-131">3.0</span></span> |
| [<span data-ttu-id="e0d6d-132">Zmiany interfejsu API JsonElement</span><span class="sxs-lookup"><span data-stu-id="e0d6d-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="e0d6d-133">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-133">3.0</span></span> |
| [<span data-ttu-id="e0d6d-134">FieldInfo.SetValue zgłasza wyjątek dla pól statycznych, tylko do init</span><span class="sxs-lookup"><span data-stu-id="e0d6d-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="e0d6d-135">3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-135">3.0</span></span> |
| [<span data-ttu-id="e0d6d-136">Pola prywatne dodane do wbudowanych typów struktur</span><span class="sxs-lookup"><span data-stu-id="e0d6d-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="e0d6d-137">2.1</span><span class="sxs-lookup"><span data-stu-id="e0d6d-137">2.1</span></span> |
| [<span data-ttu-id="e0d6d-138">Zmiana wartości domyślnej programu UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="e0d6d-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="e0d6d-139">2.1</span><span class="sxs-lookup"><span data-stu-id="e0d6d-139">2.1</span></span> |
| [<span data-ttu-id="e0d6d-140">Wersje OpenSSL w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="e0d6d-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="e0d6d-141">2.1</span><span class="sxs-lookup"><span data-stu-id="e0d6d-141">2.1</span></span> |
| [<span data-ttu-id="e0d6d-142">UnauthorizedAccessException zgłoszony przez FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="e0d6d-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="e0d6d-143">1.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-143">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="e0d6d-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-144">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="e0d6d-145">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e0d6d-145">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="e0d6d-146">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="e0d6d-146">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
