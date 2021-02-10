use_relative_paths = True

vars = {
  'chromium_url': 'https://chromium.googlesource.com',

  #
  # TODO(crbug.com/941824): The values below need to be kept in sync
  # between //DEPS and //buildtools/DEPS, so if you're updating one,
  # update the other. There is a presubmit check that checks that
  # you've done so; if you are adding new tools to //buildtools and
  # hence new revisions to this list, make sure you update the
  # _CheckBuildtoolsRevsAreInSync in PRESUBMIT.py to include the additional
  # revisions.
  #

  # GN CIPD package version.
  'gn_version': 'git_revision:55ad154c961d8326315b1c8147f4e504cd95e9e6',

  # By default, do not checkout the re-client binaries.
  'checkout_reclient': False,

  # reclient CIPD package version
  'reclient_version': 're_client_version:0.19.3.3b3042c',

  # When changing these, also update the svn revisions in deps_revisions.gni
  # TODO(crbug.com/1166332) rename to clang_format_revision.
  'clang_fmt_revision':    '99803d74e35962f63a775f29477882afd4d57d94',
  'libcxx_revision':       '8fa87946779682841e21e2da977eccfb6cb3bded',
  'libcxxabi_revision':    '196ba1aaa8ac285d94f4ea8d9836390a45360533',
  'libunwind_revision':    'd999d54f4bca789543a2eb6c995af2d9b5a1f3ed',
}

deps = {
  'clang_format/script':
    Var('chromium_url') +
    '/external/github.com/llvm/llvm-project/clang/tools/clang-format.git@' +
    Var('clang_fmt_revision'),
  'linux64': {
    'packages': [
      {
        'package': 'gn/gn/linux-amd64',
        'version': Var('gn_version'),
      }
    ],
    'dep_type': 'cipd',
    'condition': 'host_os == "linux"',
  },
  'mac': {
    'packages': [
      {
        'package': 'gn/gn/mac-amd64',
        'version': Var('gn_version'),
      }
    ],
    'dep_type': 'cipd',
    'condition': 'host_os == "mac"',
  },
  'third_party/libc++/trunk':
    Var('chromium_url') +
    '/external/github.com/llvm/llvm-project/libcxx.git' + '@' +
    Var('libcxx_revision'),
  'third_party/libc++abi/trunk':
    Var('chromium_url') +
    '/external/github.com/llvm/llvm-project/libcxxabi.git' + '@' +
    Var('libcxxabi_revision'),
  'third_party/libunwind/trunk':
    Var('chromium_url') +
    '/external/github.com/llvm/llvm-project/libunwind.git' + '@' +
    Var('libunwind_revision'),
  'win': {
    'packages': [
      {
        'package': 'gn/gn/windows-amd64',
        'version': Var('gn_version'),
      }
    ],
    'dep_type': 'cipd',
    'condition': 'host_os == "win"',
  },
  'reclient': {
    'packages': [
      {
        'package': 'infra/rbe/client/${{platform}}',
        'version': Var('reclient_version'),
      }
    ],
    'dep_type': 'cipd',
    'condition': '(host_os == "linux" or host_os == "win") and checkout_reclient',
  },
}
