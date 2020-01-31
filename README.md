```
$ env RUST_BACKTRACE=full cargo build
   Compiling missing-lifetime-ice v0.1.0 (/Users/jbr/code/missing-lifetime)
thread 'rustc' panicked at 'called `Result::unwrap()` on an `Err` value: DistinctSources(DistinctSources { begin: (Real("src/lib.rs"), BytePos(0)), end: (Real("src/my_struct.rs"), BytePos(29)) })', src/librustc_errors/lib.rs:197:29
stack backtrace:
   0:        0x10d827675 - <std::sys_common::backtrace::_print::DisplayBacktrace as core::fmt::Display>::fmt::h8db83eca50336bdb
   1:        0x10d85ad1d - core::fmt::write::h1dd60e084b1878bd
   2:        0x10d81a19b - std::io::Write::write_fmt::hff040ddf0c90252f
   3:        0x10d82bb0a - std::panicking::default_hook::{{closure}}::h30e59e050073de11
   4:        0x10d82b80a - std::panicking::default_hook::h471dc4c16e17c6ba
   5:        0x1078f4ba2 - rustc_driver::report_ice::ha38b927385db339a
   6:        0x10d82c2aa - std::panicking::rust_panic_with_hook::h9acc441fb91822a7
   7:        0x10d82bd62 - rust_begin_unwind
   8:        0x10d85793f - core::panicking::panic_fmt::h9ba960080cb7e2bf
   9:        0x10d8575d5 - core::option::expect_none_failed::h16e48eebd625a6c6
  10:        0x10b37bbfb - core::ops::function::impls::<impl core::ops::function::FnOnce<A> for &mut F>::call_once::h4037e7e013320467
  11:        0x10b36aeb1 - <alloc::vec::Vec<T> as alloc::vec::SpecExtend<T,I>>::from_iter::hc59febe08e1fbb08
  12:        0x10b35c200 - <rustc_errors::emitter::EmitterWriter as rustc_errors::emitter::Emitter>::emit_diagnostic::h197fd57a21f49d26
  13:        0x10b378e23 - <rustc_errors::json::JsonEmitter as rustc_errors::emitter::Emitter>::emit_diagnostic::h6f851b6f7cbe8ba6
  14:        0x10b3802af - rustc_errors::HandlerInner::emit_diagnostic::h6559e499f082801f
  15:        0x10b34b7ec - rustc_errors::diagnostic_builder::DiagnosticBuilder::emit::haf41cbc9cd2bb91a
  16:        0x1099a50ed - rustc_resolve::lifetimes::LifetimeContext::resolve_elided_lifetimes::h34118b651d3b825b
  17:        0x10999d744 - <rustc_resolve::lifetimes::LifetimeContext as rustc_hir::intravisit::Visitor>::visit_lifetime::h569739c63f5d4fb2
  18:        0x10999940d - <rustc_resolve::lifetimes::LifetimeContext as rustc_hir::intravisit::Visitor>::visit_ty::h6e4df70efec70df3
  19:        0x10993d54e - rustc_hir::intravisit::walk_impl_item::h6a0e152e1d7b0947
  20:        0x10999c6bb - <rustc_resolve::lifetimes::LifetimeContext as rustc_hir::intravisit::Visitor>::visit_impl_item::h707f8eb13c89f366
  21:        0x10994144d - rustc_hir::intravisit::walk_item::h893bf7e549b54151
  22:        0x109998aee - <rustc_resolve::lifetimes::LifetimeContext as rustc_hir::intravisit::Visitor>::visit_item::hdbcd8dc0fe9e29c0
  23:        0x1099967f8 - rustc_resolve::lifetimes::resolve_lifetimes::h5edd5e6fc6e3dd69
  24:        0x109913022 - rustc::ty::query::__query_compute::resolve_lifetimes::hc89338b2ceec6b93
  25:        0x1099ce0fc - rustc::dep_graph::graph::DepGraph::with_task_impl::h7a9653f4e0c4a2df
  26:        0x1098f2922 - rustc::ty::query::plumbing::<impl rustc::ty::context::TyCtxt>::get_query::h6790f40aa5919139
  27:        0x109994c79 - core::ops::function::FnOnce::call_once::h75280abd0c4da212
  28:        0x10ab66dbd - rustc::dep_graph::graph::DepGraph::with_task_impl::ha9fc94096e5ee1fc
  29:        0x10aefdfa3 - rustc::ty::query::plumbing::<impl rustc::ty::context::TyCtxt>::get_query::h69e87c5bf0e44b1f
  30:        0x10b030d8f - rustc::ty::context::TyCtxt::object_lifetime_defaults::h440cccd1eb11094f
  31:        0x109bb0833 - rustc_typeck::collect::generics_of::hb21923cce5d63053
  32:        0x109cf2e17 - rustc::ty::query::__query_compute::generics_of::hf40f63b9c62b929d
  33:        0x109c1d3bb - rustc::ty::query::<impl rustc::ty::query::config::QueryAccessors for rustc::ty::query::queries::generics_of>::compute::hcf08bb3f6bb63d57
  34:        0x109bcd56f - rustc::dep_graph::graph::DepGraph::with_task_impl::h888f92ebe37e8e16
  35:        0x109c85533 - rustc::ty::query::plumbing::<impl rustc::ty::context::TyCtxt>::get_query::he3755983402f91d3
  36:        0x109bab98d - <rustc_typeck::collect::CollectItemTypesVisitor as rustc_hir::intravisit::Visitor>::visit_item::h60dce5688768853f
  37:        0x109b92048 - rustc::hir::map::Map::visit_item_likes_in_module::hf7997abb8ae1e354
  38:        0x109baaf84 - rustc_typeck::collect::collect_mod_item_types::h1fee6a5de145936e
  39:        0x109cf48aa - rustc::ty::query::__query_compute::collect_mod_item_types::h306d6ee8be4b393b
  40:        0x109c1d96b - rustc::ty::query::<impl rustc::ty::query::config::QueryAccessors for rustc::ty::query::queries::collect_mod_item_types>::compute::h4056feaf49f72592
  41:        0x109bc5711 - rustc::dep_graph::graph::DepGraph::with_task_impl::h3ea8f2ffc9209a2c
  42:        0x109c2dccf - rustc::ty::query::plumbing::<impl rustc::ty::context::TyCtxt>::get_query::h10b4915f3931cfa9
  43:        0x109c1ddc3 - rustc::ty::query::plumbing::<impl rustc::ty::context::TyCtxt>::ensure_query::h14273f5104ae9c4e
  44:        0x109cecd5d - rustc_typeck::check_crate::h91dcd57b50b1134e
  45:        0x107ad3602 - rustc_interface::passes::analysis::hce6f4c598da4e765
  46:        0x10789a0fe - rustc::ty::query::__query_compute::analysis::h83539f9625ce7cdc
  47:        0x1078e6feb - rustc::dep_graph::graph::DepGraph::with_task_impl::hfdfe1945f0a89f25
  48:        0x1078f9a32 - rustc::ty::query::plumbing::<impl rustc::ty::context::TyCtxt>::get_query::h69c1ed70cb23b5c4
  49:        0x1078e4487 - rustc::ty::context::tls::enter_global::hba2e1b3ed8bd5f12
  50:        0x1078a71df - rustc_interface::interface::run_compiler_in_existing_thread_pool::hd80f2465803d9ba2
  51:        0x10789de79 - scoped_tls::ScopedKey<T>::set::he32ef0c68ace6e5d
  52:        0x1078956f5 - syntax::with_globals::h43666f380569b454
  53:        0x107897b3d - std::sys_common::backtrace::__rust_begin_short_backtrace::hd6fa30896b83e3a2
  54:        0x10d83b9eb - __rust_maybe_catch_panic
  55:        0x1078a91e7 - core::ops::function::FnOnce::call_once{{vtable.shim}}::ha92156fae42e4821
  56:        0x10d80c02e - <alloc::boxed::Box<F> as core::ops::function::FnOnce<A>>::call_once::hd75e9f7809bd38c6
  57:        0x10d83a95e - std::sys::unix::thread::Thread::new::thread_start::ha6b5445a5021ab98
  58:     0x7fff72bf1e65 - _pthread_start

error: internal compiler error: unexpected panic

note: the compiler unexpectedly panicked. this is a bug.

note: we would appreciate a bug report: https://github.com/rust-lang/rust/blob/master/CONTRIBUTING.md#bug-reports

note: rustc 1.42.0-nightly (d1e594f40 2020-01-22) running on x86_64-apple-darwin

note: compiler flags: -C debuginfo=2 -C incremental --crate-type lib

note: some of the compiler flags provided by cargo are hidden

query stack during panic:
#0 [resolve_lifetimes] resolving lifetimes
#1 [object_lifetime_defaults_map] looking up lifetime defaults for a region
#2 [generics_of] processing `main`
#3 [collect_mod_item_types] collecting item types in top-level module
#4 [analysis] running analysis passes on this crate
end of query stack
error: could not compile `missing-lifetime-ice`.

To learn more, run the command again with --verbose.
```
