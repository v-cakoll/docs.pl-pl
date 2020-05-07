---
title: Podstawowe zmiany w bibliotece klas podstawowych
description: Wyświetla istotne zmiany w podstawowych bibliotekach programu .NET.
ms.date: 09/20/2019
ms.openlocfilehash: a2eb4be89d78f50d201272f3449374bc27d8c785
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859930"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="5a532-103">Podstawowe zmiany w bibliotekach .NET</span><span class="sxs-lookup"><span data-stu-id="5a532-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="5a532-104">Podstawowe biblioteki .NET zapewniają pierwotne i inne typy ogólne używane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a532-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="5a532-105">Następujące istotne zmiany zostały udokumentowane na tej stronie:</span><span class="sxs-lookup"><span data-stu-id="5a532-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="5a532-106">Zmiana podziału</span><span class="sxs-lookup"><span data-stu-id="5a532-106">Breaking change</span></span> | <span data-ttu-id="5a532-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="5a532-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="5a532-108">Metody SSE i SSE2 CompareGreaterThan prawidłowo obsługują dane wejściowe NaN</span><span class="sxs-lookup"><span data-stu-id="5a532-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="5a532-109">5.0</span><span class="sxs-lookup"><span data-stu-id="5a532-109">5.0</span></span> |
| [<span data-ttu-id="5a532-110">Interfejsy API służące do raportowania wersji teraz produktu i nie wersji</span><span class="sxs-lookup"><span data-stu-id="5a532-110">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="5a532-111">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-111">3.0</span></span> |
| [<span data-ttu-id="5a532-112">Niestandardowe wystąpienia EncoderFallbackBuffer nie mogą podlegać rekursywnie</span><span class="sxs-lookup"><span data-stu-id="5a532-112">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="5a532-113">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-113">3.0</span></span> |
| [<span data-ttu-id="5a532-114">Zmiany zachowań formatowania zmiennoprzecinkowego i analizowania</span><span class="sxs-lookup"><span data-stu-id="5a532-114">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="5a532-115">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-115">3.0</span></span> |
| [<span data-ttu-id="5a532-116">Operacje analizowania zmiennoprzecinkowe nie będą już kończyć się niepowodzeniem lub nie generują wyjątku overflow</span><span class="sxs-lookup"><span data-stu-id="5a532-116">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="5a532-117">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-117">3.0</span></span> |
| [<span data-ttu-id="5a532-118">InvalidAsynchronousStateException — przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="5a532-118">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="5a532-119">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-119">3.0</span></span> |
| [<span data-ttu-id="5a532-120">Zastępowanie źle sformułowanych sekwencji bajtów w formacie UTF-8 następuje po wskazówkach dotyczących standardu Unicode</span><span class="sxs-lookup"><span data-stu-id="5a532-120">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="5a532-121">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-121">3.0</span></span> |
| [<span data-ttu-id="5a532-122">TypeDescriptionProviderAttribute przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="5a532-122">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="5a532-123">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-123">3.0</span></span> |
| [<span data-ttu-id="5a532-124">Element ZipArchiveEntry nie obsługuje już archiwów z niespójnymi rozmiarami wpisów</span><span class="sxs-lookup"><span data-stu-id="5a532-124">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="5a532-125">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-125">3.0</span></span> |
| [<span data-ttu-id="5a532-126">Typ wyjątku serializatora JSON został zmieniony z elementu Jsonexception na NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="5a532-126">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="5a532-127">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-127">3.0</span></span> |
| [<span data-ttu-id="5a532-128">Zmień semantykę (String) na wartość null w Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="5a532-128">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="5a532-129">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-129">3.0</span></span> |
| [<span data-ttu-id="5a532-130">Metody JsonEncodedText. Encode mają dodatkowy argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="5a532-130">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="5a532-131">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-131">3.0</span></span> |
| [<span data-ttu-id="5a532-132">Zmieniono sygnaturę JsonFactoryConverter. isconverter</span><span class="sxs-lookup"><span data-stu-id="5a532-132">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="5a532-133">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-133">3.0</span></span> |
| [<span data-ttu-id="5a532-134">Zmiany interfejsu API jsonelement</span><span class="sxs-lookup"><span data-stu-id="5a532-134">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="5a532-135">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-135">3.0</span></span> |
| [<span data-ttu-id="5a532-136">Element FieldInfo. SetValue zgłasza wyjątek dla pól static, tylko init</span><span class="sxs-lookup"><span data-stu-id="5a532-136">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="5a532-137">3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-137">3.0</span></span> |
| [<span data-ttu-id="5a532-138">Pola prywatne dodane do wbudowanych typów struktur</span><span class="sxs-lookup"><span data-stu-id="5a532-138">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="5a532-139">2.1</span><span class="sxs-lookup"><span data-stu-id="5a532-139">2.1</span></span> |
| [<span data-ttu-id="5a532-140">Zmień wartość domyślną UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="5a532-140">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="5a532-141">2.1</span><span class="sxs-lookup"><span data-stu-id="5a532-141">2.1</span></span> |
| [<span data-ttu-id="5a532-142">Wersje OpenSSL na macOS</span><span class="sxs-lookup"><span data-stu-id="5a532-142">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="5a532-143">2.1</span><span class="sxs-lookup"><span data-stu-id="5a532-143">2.1</span></span> |
| [<span data-ttu-id="5a532-144">UnauthorizedAccessException zgłoszone przez FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="5a532-144">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="5a532-145">1.0</span><span class="sxs-lookup"><span data-stu-id="5a532-145">1.0</span></span> |
| [<span data-ttu-id="5a532-146">Obsługa wyjątków uszkodzonego stanu procesu nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="5a532-146">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="5a532-147">1.0</span><span class="sxs-lookup"><span data-stu-id="5a532-147">1.0</span></span> |
| [<span data-ttu-id="5a532-148">Właściwości UriBuilder nie dołączają już znaków wiodących</span><span class="sxs-lookup"><span data-stu-id="5a532-148">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="5a532-149">1.0</span><span class="sxs-lookup"><span data-stu-id="5a532-149">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="5a532-150">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5a532-150">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="5a532-151">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5a532-151">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="5a532-152">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5a532-152">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="5a532-153">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5a532-153">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***
