c_scheds = ['scx_simple']

c_scheds_lib = []

thread_dep = dependency('threads')

foreach sched: c_scheds
  bpf_o = gen_bpf_o.process(sched + '.bpf.c')
  bpf_skel = gen_bpf_skel.process(bpf_o)
  executable(sched, [bpf_skel, sched + '.c'],
             dependencies: [kernel_dep, libbpf_dep, thread_dep, user_c_dep],
             install: true)
endforeach

foreach sched: c_scheds_lib
  bpf_o = gen_bpf_o.process(sched + '.bpf.c')
  bpf_skel = gen_bpf_skel_lib.process(bpf_o)
  executable(sched, [bpf_skel, sched + '.c'],
             dependencies: [kernel_dep, libbpf_dep, thread_dep, user_c_dep],
             install: true)
endforeach
