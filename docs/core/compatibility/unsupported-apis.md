---
title: Nieobsługiwane interfejsy API w usłudze .NET Core
titleSuffix: ''
description: Dowiedz się, które interfejsy API z platformy .NET Framework, które zawsze zgłaszają wyjątek w .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: c4b94321d30cacd90d5c2ee23c258681683a6faa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092970"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="b4043-103">Interfejsy API, które zawsze zgłaszają wyjątki w uspolonym .NET Core</span><span class="sxs-lookup"><span data-stu-id="b4043-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="b4043-104">Następujące interfejsy API <xref:System.PlatformNotSupportedException> zawsze będą zgłaszać na .NET Core na wszystkich lub podzbiór platform.</span><span class="sxs-lookup"><span data-stu-id="b4043-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="b4043-105">W tym artykule organizatorzy organizują elementy członkowskie interfejsu API, których dotyczy problem, według obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="b4043-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="b4043-106">Ten artykuł jest w toku.</span><span class="sxs-lookup"><span data-stu-id="b4043-106">This article is a work-in-progress.</span></span> <span data-ttu-id="b4043-107">Nie jest to pełna lista interfejsów API, które zgłaszają wyjątki w .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b4043-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="b4043-108">Ten artykuł nie zawiera jawnych implementacji interfejsu dla serializacji binarnej, które wyrzucając na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b4043-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="b4043-109">Aby uzyskać więcej informacji, zobacz [Serializacja binarna w .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="b4043-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="b4043-110">System</span><span class="sxs-lookup"><span data-stu-id="b4043-110">System</span></span>

| <span data-ttu-id="b4043-111">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-111">Member</span></span> | <span data-ttu-id="b4043-112">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-113">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="b4043-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="b4043-115">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="b4043-116">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-117">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="b4043-118">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="b4043-119">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="b4043-120">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-121">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b4043-122">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="b4043-123">System.CodeDom.Kompilator</span><span class="sxs-lookup"><span data-stu-id="b4043-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="b4043-124">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-124">Member</span></span> | <span data-ttu-id="b4043-125">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-126">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-127">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-128">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="b4043-129">System.collections.specialized</span><span class="sxs-lookup"><span data-stu-id="b4043-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="b4043-130">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-130">Member</span></span> | <span data-ttu-id="b4043-131">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-132">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-133">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b4043-134">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="b4043-135">System.configuration</span><span class="sxs-lookup"><span data-stu-id="b4043-135">System.Configuration</span></span>

| <span data-ttu-id="b4043-136">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-136">Member</span></span> | <span data-ttu-id="b4043-137">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b4043-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(wszyscy członkowie)</span><span class="sxs-lookup"><span data-stu-id="b4043-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="b4043-139">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="b4043-140">System.console</span><span class="sxs-lookup"><span data-stu-id="b4043-140">System.Console</span></span>

| <span data-ttu-id="b4043-141">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-141">Member</span></span> | <span data-ttu-id="b4043-142">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="b4043-143">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-143">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-145">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-145">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-147">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-147">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-149">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-149">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(tylko dostać)</span><span class="sxs-lookup"><span data-stu-id="b4043-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b4043-151">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-152">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-153">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-154">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-154">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-155"><xref:System.Console.Title?displayProperty=nameWithType>(tylko dostać)</span><span class="sxs-lookup"><span data-stu-id="b4043-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b4043-156">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-156">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-158">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-158">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-160">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-160">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-162">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-162">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-164">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="b4043-165">System.Data.Common (System.Data.Common)</span><span class="sxs-lookup"><span data-stu-id="b4043-165">System.Data.Common</span></span>

| <span data-ttu-id="b4043-166">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-166">Member</span></span> | <span data-ttu-id="b4043-167">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b4043-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(rzuty) <xref:System.NotSupportedException></span><span class="sxs-lookup"><span data-stu-id="b4043-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="b4043-169">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="b4043-170">System.Diagnostics.Process (Diagnostyka.Proces)</span><span class="sxs-lookup"><span data-stu-id="b4043-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="b4043-171">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-171">Member</span></span> | <span data-ttu-id="b4043-172">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b4043-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-174">Linux</span><span class="sxs-lookup"><span data-stu-id="b4043-174">Linux</span></span> |
| <span data-ttu-id="b4043-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-176">Linux</span><span class="sxs-lookup"><span data-stu-id="b4043-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="b4043-177">macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="b4043-178">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-179">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="b4043-180">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="b4043-181">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="b4043-182">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="b4043-183">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-183">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-185">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-185">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(tylko dostać)</span><span class="sxs-lookup"><span data-stu-id="b4043-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b4043-187">macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-187">macOS</span></span> |
| <span data-ttu-id="b4043-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-189">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="b4043-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="b4043-190">System.IO</span></span>

| <span data-ttu-id="b4043-191">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-191">Member</span></span> | <span data-ttu-id="b4043-192">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-193">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-194">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="b4043-195">System.IO.Rury</span><span class="sxs-lookup"><span data-stu-id="b4043-195">System.IO.Pipes</span></span>

| <span data-ttu-id="b4043-196">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-196">Member</span></span> | <span data-ttu-id="b4043-197">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="b4043-198">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="b4043-199">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="b4043-200">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="b4043-201">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-201">Linux and macOS</span></span> |
| <span data-ttu-id="b4043-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-203">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="b4043-204">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="b4043-205">System.Media (System.Media)</span><span class="sxs-lookup"><span data-stu-id="b4043-205">System.Media</span></span>

| <span data-ttu-id="b4043-206">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-206">Member</span></span> | <span data-ttu-id="b4043-207">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-208">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="b4043-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="b4043-209">System.Net</span></span>

| <span data-ttu-id="b4043-210">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-210">Member</span></span> | <span data-ttu-id="b4043-211">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="b4043-212">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="b4043-213">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-214">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-215">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-216">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-217">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-218">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-219">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-220">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-221">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-222">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="b4043-223">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-224">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-225">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-226">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-227">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-228">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="b4043-229">System.Net.NetworkInformacje</span><span class="sxs-lookup"><span data-stu-id="b4043-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="b4043-230">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-230">Member</span></span> | <span data-ttu-id="b4043-231">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="b4043-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="b4043-233">System.net.sockets</span><span class="sxs-lookup"><span data-stu-id="b4043-233">System.Net.Sockets</span></span>

| <span data-ttu-id="b4043-234">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-234">Member</span></span> | <span data-ttu-id="b4043-235">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)?displayProperty=nameWithType> | <span data-ttu-id="b4043-236">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="b4043-237">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="b4043-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="b4043-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="b4043-239">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-239">Member</span></span> | <span data-ttu-id="b4043-240">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="b4043-241">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="b4043-242">System.reflection</span><span class="sxs-lookup"><span data-stu-id="b4043-242">System.Reflection</span></span>

| <span data-ttu-id="b4043-243">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-243">Member</span></span> | <span data-ttu-id="b4043-244">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-245">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4043-246">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-247">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b4043-248">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4043-249">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-250">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="b4043-251">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="b4043-252">System.runtime.compilerservices</span><span class="sxs-lookup"><span data-stu-id="b4043-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="b4043-253">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-253">Member</span></span> | <span data-ttu-id="b4043-254">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="b4043-255">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="b4043-256">System.runtime.interopservices</span><span class="sxs-lookup"><span data-stu-id="b4043-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="b4043-257">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-257">Member</span></span> | <span data-ttu-id="b4043-258">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b4043-259">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="b4043-260">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="b4043-261">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="b4043-262">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4043-263">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="b4043-264">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="b4043-265">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="b4043-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="b4043-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="b4043-267">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-267">Member</span></span> | <span data-ttu-id="b4043-268">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="b4043-269">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="b4043-270">System.Bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="b4043-270">System.Security</span></span>

| <span data-ttu-id="b4043-271">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-271">Member</span></span> | <span data-ttu-id="b4043-272">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="b4043-273">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="b4043-274">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4043-275">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="b4043-276">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="b4043-277">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="b4043-278">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="b4043-279">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="b4043-280">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="b4043-281">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="b4043-282">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="b4043-283">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b4043-284">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="b4043-285">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="b4043-286">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="b4043-287">System.security.claims</span><span class="sxs-lookup"><span data-stu-id="b4043-287">System.Security.Claims</span></span>

| <span data-ttu-id="b4043-288">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-288">Member</span></span> | <span data-ttu-id="b4043-289">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="b4043-290">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-291">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="b4043-292">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-293">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-294">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="b4043-295">System.security.cryptography</span><span class="sxs-lookup"><span data-stu-id="b4043-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="b4043-296">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-296">Member</span></span> | <span data-ttu-id="b4043-297">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4043-298">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-299">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="b4043-300">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="b4043-301">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="b4043-302">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="b4043-303">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="b4043-304">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="b4043-305">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="b4043-306">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="b4043-307">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="b4043-308">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="b4043-309">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="b4043-310">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="b4043-311">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b4043-312">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="b4043-313">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4043-314">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-315">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-316">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-317">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b4043-318">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4043-319">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-320">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-321">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b4043-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-322">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-323">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b4043-324">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b4043-325">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="b4043-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="b4043-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="b4043-327">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-327">Member</span></span> | <span data-ttu-id="b4043-328">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="b4043-329">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b4043-330">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="b4043-331">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="b4043-332">Certyfikaty System.Security.Cryptography.X509</span><span class="sxs-lookup"><span data-stu-id="b4043-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="b4043-333">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-333">Member</span></span> | <span data-ttu-id="b4043-334">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-335">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-336">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-337">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-337">All</span></span> |
| <span data-ttu-id="b4043-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="b4043-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b4043-339">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="b4043-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="b4043-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="b4043-341">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-341">Member</span></span> | <span data-ttu-id="b4043-342">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-343">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="b4043-344">System.Security.Policy (System.Security.Policy)</span><span class="sxs-lookup"><span data-stu-id="b4043-344">System.Security.Policy</span></span>

| <span data-ttu-id="b4043-345">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-345">Member</span></span> | <span data-ttu-id="b4043-346">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-347">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="b4043-348">Kontroler system.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="b4043-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="b4043-349">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-349">Member</span></span> | <span data-ttu-id="b4043-350">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-351">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="b4043-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="b4043-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="b4043-353">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-353">Member</span></span> | <span data-ttu-id="b4043-354">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-355">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="b4043-356">System.threading</span><span class="sxs-lookup"><span data-stu-id="b4043-356">System.Threading</span></span>

| <span data-ttu-id="b4043-357">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-357">Member</span></span> | <span data-ttu-id="b4043-358">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-359">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b4043-360">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="b4043-361">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="b4043-362">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="b4043-363">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="b4043-364">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="b4043-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="b4043-365">System.Xml</span></span>

| <span data-ttu-id="b4043-366">Członek</span><span class="sxs-lookup"><span data-stu-id="b4043-366">Member</span></span> | <span data-ttu-id="b4043-367">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="b4043-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="b4043-368">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="b4043-369">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b4043-370">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4043-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="b4043-371">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4043-371">See also</span></span>

- [<span data-ttu-id="b4043-372">Przełomowe zmiany migracji z platformy .NET Framework do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="b4043-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="b4043-373">Serializacja binarna w ustom .NET Core</span><span class="sxs-lookup"><span data-stu-id="b4043-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="b4043-374">Analizator przenoszenia .NET</span><span class="sxs-lookup"><span data-stu-id="b4043-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
